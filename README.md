# Deploying-web-application-using-AWS-Services
1. Launch EC2 Instance –
Create an AWS EC2 instance (Amazon Linux t2.micro) and configure key pairs for secure access.


2. Set Up Security Groups –
Allow inbound rules for SSH (port 22) and HTTP (port 80) to enable remote access and web traffic.


3. Connect to Instance –
Use PuTTY or AWS CloudShell to connect to the EC2 instance using the public IP address.


4. Install Docker –
Run commands:

sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
docker --version


5. Build Docker Image –
Create a project directory with a Dockerfile and index.html, then build the image using:

docker build -t myapp .


6. Run Docker Container –
Test the container locally using:

docker run -d -p 80:80 myapp


7. Create ECR Repository –
In AWS ECR, create a private repository to store Docker images.


8. Push Image to ECR –
Authenticate Docker with AWS and push the built image:

aws ecr get-login-password | docker login ...
docker tag myapp:latest <repo-url>/myapp:latest
docker push <repo-url>/myapp:latest


9. Create ECS Cluster & Task Definition –
Define a task using the ECR image and launch it on AWS Fargate for serverless deployment.


10. Set Up Load Balancer (Optional) –
Configure an Application Load Balancer (ALB) in EC2 to distribute traffic across ECS tasks for scalability.
