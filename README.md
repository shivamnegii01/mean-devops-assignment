Project Overview

This project demonstrates the complete containerization, cloud deployment, and CI/CD automation of a full-stack MEAN (MongoDB, Express, Angular, Node.js) application.

The application is containerized using Docker, orchestrated using Docker Compose, deployed on AWS EC2, and automated through GitHub Actions for continuous integration and continuous deployment.

Architecture Overview

The deployment architecture follows this flow:

Developer → GitHub Repository → GitHub Actions CI/CD Pipeline → Docker Hub → AWS EC2 (Ubuntu) → Docker Compose → Nginx Reverse Proxy (Port 80) → Frontend → Backend → MongoDB

Technology Stack

Angular 15 (Frontend)

Node.js with Express (Backend)

MongoDB (Database)

Docker

Docker Compose

Nginx (Reverse Proxy)

AWS EC2 (Ubuntu 22.04)

GitHub Actions (CI/CD)

Containerization Strategy
Backend Service

Built using Node.js and Express

Exposed internally on port 5000

Connected to MongoDB service through Docker network

Frontend Service

Angular production build generated during Docker build stage

Served using Nginx container

Database Service

Official MongoDB Docker image

Persistent volume configured for data durability

Reverse Proxy

Nginx configured to expose application on port 80

Routes traffic to frontend and backend services

Cloud Deployment

The application is deployed on an AWS EC2 instance with the following configuration:

Instance Type: t3.micro

Operating System: Ubuntu 22.04

Docker and Docker Compose installed

Security Group configured with:

Port 22 (SSH)

Port 80 (HTTP)

Docker Compose is used on the EC2 instance to manage multi-container services.

CI/CD Implementation

Continuous Integration and Continuous Deployment are implemented using GitHub Actions.

Trigger Condition

Push to the main branch

Pipeline Workflow

Checkout repository code

Authenticate with Docker Hub

Build backend Docker image

Build frontend Docker image

Push images to Docker Hub

Establish secure SSH connection to EC2

Pull latest Docker images

Restart containers using Docker Compose

Deployment is fully automated and requires no manual server intervention.

Security Configuration

Docker Hub authentication handled via Personal Access Token

SSH private key securely stored in GitHub repository secrets

EC2 Security Group configured with restricted access

No hardcoded credentials in source code

Verification and Testing

The deployment was verified through:

Successful GitHub Actions workflow execution

Docker images available in Docker Hub registry

Running containers verified via docker ps on EC2

Application accessible publicly through EC2 public IP on port 80

Project Outcome

Successfully containerized full-stack MEAN application

Implemented multi-service architecture using Docker Compose

Deployed application to AWS EC2

Configured Nginx as reverse proxy

Built fully automated CI/CD pipeline

Achieved automated production deployment workflow

Author

Shivam Negi
