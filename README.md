# Setup Nexus with Apt

1. Describe how to setup nexus repository.
    
    1. Pull docker
    ```
    docker pull sonatype/nexus3
    ```

    2. Create Volume
    ```
    docker volume create --name nexus-data
    ```
    3. Start docker
    ```
     docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
    ``` 
2. Create Apt Repo
    
    1. login to 
        ```
        http://envy-vm.lan:808/
        ```
    2. Click Gear Icon and Create Repository
    
        http://envy-vm.lan:8081/#admin/repository/repositories

    3. Setup GPG Keys

        https://help.sonatype.com/repomanager3/nexus-repository-administration/formats/apt-repositories
    
    4. Upload private.gpg.key

3. Add repo to apt
    
   ```
   deb http://envy-vm.lan:8081/repository/envy-apt/ focal main
   ```

4. Create a package following this guide:

    https://askubuntu.com/questions/1130558/how-to-build-deb-package-for-ubuntu-18-04

    1. I did a amd64 package.

5. Upload package using UI

    http://envy-vm.lan:8081/#browse/browse:envy-apt

6. Update apt

    ```
    sudo apt update
    ```

7. Your package should exit.

    ```
    sudo apt install helloworld
    ```

References:

https://hub.docker.com/r/sonatype/nexus3/

https://askubuntu.com/questions/1130558/how-to-build-deb-package-for-ubuntu-18-04
