# Online Shop 🛍️ for Hackathon Phase 1


## 📋 Steps to Set Up and Run the Project

## 👇FOR AWS USERS and LOCAL USERS

### 0️⃣ Logged in on AWS Console
- Logged into the AWS Console and started an instance with **Ubuntu**.
- Saved the key pair for secure access.

### 1️⃣ Allow port
- Allow 3000 port which will be used in this project
- click on instance and navigate to security group then edit inbound rules then add rule then add 3000 port then set it to all ipv4 then save

### 2️⃣ Connected with Local Machine
- Ensured the key is not publicly viewable using:
  ```bash
  chmod 400 (downloaded key name)
  ```
- Connected the instance with the local machine using **SSH**.

### 3️⃣ System Update
- Updated the system with:
  ```bash
  sudo apt update
  ```

### 4️⃣ Forked the Hackathon Repository
- Forked the original Hackathon repository to my GitHub account for independent work.

### 5️⃣ Created a New User for the Project
- Created a user named `hackathonuser`:
  ```bash
  sudo useradd -m hackathonuser
  ```
- Granted Sudo access:
  ```bash
  sudo usermod -aG sudo hackathonuser
  ```
- Switch to hackathonuser:
  ```bash
  su - hackathonuser
  ```

### 6️⃣ Installed Docker 🐳
- Installed Docker using:
  ```bash
  sudo apt-get install docker.io
  ```

### 7️⃣ Verified Docker Installation ✅
- Checked if Docker is running:
  ```bash
  sudo systemctl status docker
  ```

### 8️⃣ Added Current User to Docker Group 👤
- Added current user to the Docker group:
  ```bash
  sudo usermod -aG docker $USER
  ```

### 9️⃣ Refreshed User Groups 🔄
- Applied changes to user groups:
  ```bash
  newgrp docker
  ```

### 🔟 Cloned the Hackathon Repository Locally 🛠️
- Cloned the forked repository to my instance generated a personal access token (PAT) from Settings > Developer Settings > PAT > Tokens for authentication:
  ```bash
  git clone https://username:PAT@github.com//online_shop.git
  ```

### 🔢 Reviewed Source Code and Created a Dockerfile 📂
- Analyzed the source code and created a `Dockerfile` using `vim`:
  ```bash
  vim Dockerfile
  ```

  ```bash
  # Alpine is chosen for its lightweight nature, which helps reduce the image size
  FROM node:18-alpine

  # Setting the working directory inside the container
  WORKDIR /app

  # Copy package.json and package-lock.json to the working directory
  COPY package*.json ./
  
  # Install dependencies specified in package.json
  RUN npm install

  # Copy the rest of the application code into the working directory
  COPY . .

  # Build the app
  RUN npm run build

  # Set environment variable
  ENV PORT=3000

  # Exposing port 3000 to allow external access to the application
  EXPOSE 3000

  # Here, it starts a development server using npm's "start" script
  CMD ["npm", "run", "dev", "--", "--port", "3000"]
  ```

### 🔢 Built the Docker Image 🏗️
- Built a Docker image of the project:
  ```bash
  docker build -t online-shop .
  ```

### 🔢 Ran the Application in a Container 🖥️
- Ran a container from the built image, mapping it to port `3000` on the host machine:
  ```bash
  docker run -d -p 3000:3000 online-shop
  ```

 ![alt text](<Screenshot 2025-02-21 030903.png>)
![alt text](<Screenshot 2025-02-21 030949.png>)
- The application is accessible at: `http://IP:3000/`.

### 🔢 Stop and delete container and Images 🖥️
- Stop the runnig container
  ```bash
  docker stop container_id
  ```
- Delete the runnig container
  ```bash
  docker rm container_id
  ```
- Show all the container
  ```bash
  docker ps -a
  ```

- Show all Images
  ```bash
  docker images
  ```
- Delete the images
  ```bash
  docker rmi image_name or image_id
  ```
---
## Explained video Link of this Hackathon Project 
https://drive.google.com/file/d/1rU8-HQiP6Yk6pJmxt__FOj7Rktyz6wJT/view?usp=drive_link