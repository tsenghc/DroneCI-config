# Drone CI Installation Guide
## System Requirements

> Ubuntu 24.04 LTS

## Installation Steps
### 1.Install Docker

```bash
sudo apt install docker.io -y

# Add current user to docker group
sudo usermod -aG docker ubuntu
```
### 2.Reload group settings
```bash
newgrp docker
```
### 3.Install Docker Compose
```bash
# Download latest version of Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# Set execute permission
sudo chmod +x /usr/local/bin/docker-compose
# Verify installation
docker-compose --version
```

### 4.Configure Environment Variables
```bash
# Create .env file with the following content:
DRONE_SERVER_HOST={your-domain}
DRONE_SERVER_PROTO=https
DRONE_RPC_HOST=drone-server
DRONE_RPC_PROTO=http
DRONE_RPC_SECRET={openssl rand -hex 16}
DRONE_GITHUB_CLIENT_ID=
DRONE_GITHUB_CLIENT_SECRET=
ADMIN= # your github username
DRONE_DATA=./drone # Volume mapping path

```
## Troubleshooting
* If permission errors occur, make sure you've run newgrp docker
* If unable to connect to Docker Hub, check network settings
* If environment variables are not loading, verify .env file format

## Additional Resources

Drone CI Documentation: https://docs.drone.io/server/provider/github/
