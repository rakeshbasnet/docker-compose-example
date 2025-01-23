# Docker Compose Example

## Project Setup Instructions

### Prerequisites
- Python 3.10.12 installed
- Flask 3.0.3 installed (already added in requirements.txt)

### Step-by-Step Guide

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/rakeshbasnet/docker-compose-example.git
   cd docker-compose-example

2. **Copy .env.example File to Create .env File**:
    ```bash
    cp .env.example .env

2. **Set Up Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   

5. **Run the Development Server**:
   ```bash
   python main.py

6. **Access the Application**:
   Open a browser and go to: `http://127.0.0.1:5000`


## Docker Compose and Docker containers

### Prerequisites
- Docker installed
- Docker Compose installed

### Step-by-Step Guide

1. **Build Application Docker Image from Dockerfile**:
    ```bash
    docker build -t image-name:tag-name .    //replace your flask-app-image-name and tag name

2. **Create Docker Network**:
    ```bash
    docker network ls  // to list all the networks in docker
    docker network create flask-app-network     //create new network

3. **Run Docker Compose**:
    ```bash
    docker compose up -d // -d: runs the containers in detached mode

4. **To Stop the running Conatainers**:
    ```bash
    docker compose down

## Accessing Applications:
1. Before Accessing the Application, Access pgAdmin in `http://localhost:8080`.
2. Login using the credential passed during container creation.
3. On right top, right click `Servers`, Click `Create->Server Group` and Save.
4. Right Click on recently created Server, Click `Register->Server-> Connection Tab`, Add Postgres Credentials and Connect. If Connection is successful, the docker network is working.
***Note***: For host section in Connection tab, add the db container name and other credentials passed via env files.
5. Look for mydb inside Server and add `users table` with some data.
6. Now, Access the Flask Application in `http://localhost:5000`
7. To make sure it is correctly connected with db:
Check URL: `http://localhost:5000/users`, a list of users will retun.
8. To check whether, it is correctly connected with redis cache server,
Check URL: `http://localhost:5000/cache`, it will return a message: `Cache Hit: b'Hello from Redis Cache!'`