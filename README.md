# HRMS_Deployment-Docker

docker Install-setup
-------------------
 

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y ca-certificates curl gnupg lsb-release

# Add Docker GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Add Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io \
docker-buildx-plugin docker-compose-plugin
 

# Allow docker without sudo
sudo usermod -aG docker ubuntu
exit

# Start & enable Docker
sudo systemctl start docker
sudo systemctl enable docker
Docker images

-------------------------------------Docker-COMMANDS----------------
- docker images -> check image present or not
-docker ps ->show running container
-docker ps -a -> show all container
- docker  run -it ubuntu /bin/bash  ->docker image install  <ubuntu>
- docker  run -it --name shubham   ubuntu /bin/bash-> creat container
- cat /etc/os-release  ->check which ubuntu,linux run
-docker images->check images on docker
-docker pull jenkins-> only want in docker not run in future we use
 docker search <ubuntu,linux,jenkins> -> whithout go docker hub search 
- docker  run -it --name shubham   ubuntu /bin/bash->chnge container name
-docker start/stop shubham ->start/stop perticular container
-docker attach shubham->go in container
- docker rm shubham->delete container->1st stop then delete->when exit automatic stop

*3 ways to make img

How to create container to image image to container
------------------------------------------------------
*How to create container -:-
-------------------------
1)-docker run --name shubham -it ubuntu/bin/bash->create container with name
-ls->cd tmp->touch<create file> ->afer made container made  img from this container 


*made image from container
---------------------------
docker commit <container name> updateimg

* again made container from  image-
--------------------------------
- docker  run -it --name shubham   ubuntu /bin/bash ->create container 

*how to make vi file for docker-
vi Docker 
---------

FROM ubuntu
WORKDIR /tmp->where we want work 
RUN echo "Jay Shri Ram" > /temp/testfile  ->what print in docker file
ENV myname shubham_kumbhar -> what who chnge 
COPY testfile /tmp-> copy file from container
ADD test.tar.gz /tmp-> copy from docker ub

* make imge from Docker file
---------------------------------
-docker build -t test . -> build img from Dockerfile 

*Make container from from img
--------------------------------
- docker  run -it --name shubham   ubuntu /bin/bash

----------------------------------------------------------
*create volume
-------------
1)make docker file
vi Dockerfile
FROM ubuntu
VOLUME ["/volume-file-name"]
:wq

2)-docker build -t <imgename> -> make img from docker file
3)-docker  run -it --name shubham   <img name>/bin/bash ->create contner
4)-docker  run -it --name cont2 --privileged=true --volumes-from cont1 ubuntu /bin/bash->share volume of cont1 to cont2

* create volume by using command
---------------------------------
- docker run -it --name hostcont -v /home/ec2-user:/skk --privileged ubuntu /bin/bash->connect host to cont
-









