1. Project Title and Description

markdown
# ECR-ECS Project - Dockerized Web Application

A static website containerized with Docker, deployed on AWS ECR and ECS. This project demonstrates the complete containerization workflow from Dockerfile creation to cloud deployment.
2. Table of Contents

markdown
## Table of Contents
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Docker Setup](#docker-setup)
  - [Building the Docker Image](#building-the-docker-image)
  - [Running the Container](#running-the-container)
  - [Port Mapping](#port-mapping)
- [Local Testing](#local-testing)
- [AWS ECR Deployment](#aws-ecr-deployment)
- [AWS ECS Deployment](#aws-ecs-deployment)
- [Troubleshooting](#troubleshooting)
- [Author](#author)
3. Prerequisites Section

markdown
## Prerequisites

- Docker Desktop installed on your local machine
- AWS CLI configured with appropriate credentials
- AWS Account with ECR and ECS access
- Basic knowledge of Docker commands
4. Project Structure

markdown
## Project Structure
ECR-ECS-Project/
├── Dockerfile
├── buildspec.yml
├── index.html
├── about.html
├── contact.html
├── service.html
├── guard.html
├── css/
├── js/
├── images/
└── fonts/

text
5. Docker Setup Section (Based on your history)

markdown
## Docker Setup

### Creating Dockerfile
The project includes a Dockerfile that defines the container configuration:

```dockerfile
# Example Dockerfile content (replace with your actual content)
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
Building the Docker Image

bash
docker build -t my-app:latest .
Running the Container

bash
docker run -itd --name cont-1 -p 80:80 my-app:latest
Docker Management Commands

bash
# List running containers
docker ps

# List all containers
docker ps -a

# Stop a container
docker stop <container-id>

# Remove a container
docker rm <container-id>

# Remove an image
docker image rm <image-id>
text

### 6. **Local Testing Section**
```markdown
## Local Testing

After running the container, access your application at:
http://localhost/index.html
http://localhost/about.html
http://localhost/contact.html
http://localhost/service.html
http://localhost/guard.html

text

### Verify Container Status
```bash
docker ps
docker images
text

### 7. **AWS ECR Deployment**
```markdown
## AWS ECR Deployment

### Tag the Docker Image
```bash
docker tag my-app:latest <aws-account-id>.dkr.ecr.<region>.amazonaws.com/my-app:latest
Push to ECR

bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <aws-account-id>.dkr.ecr.<region>.amazonaws.com
docker push <aws-account-id>.dkr.ecr.<region>.amazonaws.com/my-app:latest
text

### 8. **AWS ECS Deployment**
```markdown
## AWS ECS Deployment

The project includes a `buildspec.yml` file for AWS CodeBuild integration with ECS deployment.

### Deployment Steps:
1. Create ECS Cluster
2. Create Task Definition
3. Create ECS Service
4. Configure Load Balancer (if needed)
5. Set up Auto-scaling rules
9. Troubleshooting Section

markdown
## Troubleshooting

### Common Issues and Solutions:

#### Port Already in Use
```bash
# Check if port 80 is in use
sudo lsof -i :80
# Stop the conflicting container
docker stop <container-id>
Container Not Starting

bash
# Check container logs
docker logs cont-1
Image Build Issues

bash
# Remove dangling images
docker image prune
# Rebuild with no cache
docker build --no-cache -t my-app:latest .
text

### 10. **Author and License**
```markdown
## Author

**Indrasurya**  
GitHub: [@indrasurya](https://github.com/indrasurya)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Docker Documentation
- AWS ECR/ECS Documentation
Complete README.md Template

Here's a complete template you can use:

markdown
# ECR-ECS Project - Dockerized Web Application

A static website containerized with Docker, deployed on AWS ECR and ECS.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Docker Setup](#docker-setup)
- [Local Testing](#local-testing)
- [AWS Deployment](#aws-deployment)
- [Commands Reference](#commands-reference)
- [Troubleshooting](#troubleshooting)
- [Author](#author)

## Prerequisites
- Docker Desktop
- AWS CLI
- AWS Account with ECR/ECS access

## Project Structure
ECR-ECS-Project/
├── Dockerfile # Container configuration
├── buildspec.yml # AWS CodeBuild specification
├── index.html # Main entry point
├── about.html
├── contact.html
├── service.html
├── guard.html
├── css/ # Stylesheets
├── js/ # JavaScript files
├── images/ # Image assets
└── fonts/ # Font files

text

## Quick Start

1. **Clone the repository**
```bash
git clone <your-repo-url>
cd ECR-ECS-Project
Build Docker image
bash
docker build -t my-app:latest .
Run container
bash
docker run -itd --name cont-1 -p 80:80 my-app:latest
Access application
Open browser and navigate to http://localhost
Docker Setup

Build the Image

bash
docker build -t my-app:latest .
Run Container with Port Mapping

bash
docker run -itd --name cont-1 -p 80:80 my-app:latest
Docker Commands Used

bash
# View running containers
docker ps

# View all containers
docker ps -a

# Stop container
docker stop cont-1

# Remove container
docker rm cont-1

# Remove image
docker rmi my-app:latest

# View images
docker images
Local Testing

Access your application:

Home: http://localhost/index.html
About: http://localhost/about.html
Contact: http://localhost/contact.html
Services: http://localhost/service.html
Guard Page: http://localhost/guard.html
AWS Deployment

ECR Setup

Create repository in ECR
Authenticate Docker to ECR
Tag and push image
ECS Setup

Create ECS cluster
Define task with container configuration
Create service with desired task count
Commands Reference

Command	Description
docker build -t my-app:latest .	Build Docker image
docker run -itd --name cont-1 -p 80:80 my-app:latest	Run container in detached mode
docker ps	List running containers
docker stop <container-id>	Stop running container
docker rm <container-id>	Remove container
docker images	List Docker images
docker image rm <image-id>	Remove Docker image
Troubleshooting

Issue: Port 80 already in use

bash
sudo lsof -i :80  # Find process using port
docker stop <container-id>  # Stop conflicting container
Issue: Container won't start

bash
docker logs cont-1  # Check container logs
Issue: Build fails

bash
docker build --no-cache -t my-app:latest .  # Rebuild without cache
Author

Indrasurya

GitHub: @indrasurya
Note: This project was developed as part of ECR-ECS learning and deployment exercise.

text

This README provides comprehensive documentation based on your actual Docker commands and project structure. Make sure to replace placeholder content (like AWS account IDs, regions) with your actual values when deploying to AWS.
