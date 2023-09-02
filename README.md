AlienVault :
https://otx.alienvault.com/
OpenCTI Docker:
https://github.com/OpenCTI-Platform/docker/blob/master/docker-compose.yml
OpenCTI env Variabe:
https://github.com/OpenCTI-Platform/docker/blob/master/.env.sample

Step 1: (Update the repositories)
sudo apt-get update

Step 2:
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
	
Step 3:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Step 4: 
sudo apt-key fingerprint 0EBFCD88

Step 5: 
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
Step 6:
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose

Step 7: 
sudo docker version

Step 8:
sudo usermod -aG docker $USER

Step 9:
docker swarm init --advertise-addr <MANAGER-IP>

Step 10:
docker swarm join --token <LONG-TOKEN-ID> <IP-ADDRESS-OF-MANAGER:PORT>

Step 11:
mkdir -p /opt/portainer && cd /opt/portainer
curl -L https://downloads.portainer.io/portainer-agent-stack.yml -o portainer-agent-stack.yml

Step 12:
docker stack deploy --compose-file=portainer-agent-stack.yml portainer
