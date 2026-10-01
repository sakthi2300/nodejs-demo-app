Node.js Demo App --- CI/CD Pipeline
A sample Node.js application with a Docker-based CI/CD pipeline using
GitHub Actions and Docker Hub.
Project Overview
This project demonstrates an automated workflow that runs when code is
pushed to the `main` branch:
Check out the source code from GitHub.
Set up Node.js 22.
Install dependencies with `npm ci`.
Run the application test (`npm test`).
Build a Docker image.
Authenticate with Docker Hub using GitHub Actions secrets.
Push the Docker image to Docker Hub.
Tech Stack
Node.js 22
Express
Docker
GitHub
GitHub Actions
Docker Hub
Application Endpoints
`GET /` --- returns `Hello! Node.js CI/CD is working.`
`GET /health` --- returns `{"status":"OK"}`
Run Locally
Install dependencies:
``` bash
npm ci
```
Run the tests:
``` bash
npm test
```
Start the application:
``` bash
npm start
```
Open `http://localhost:3000` in your browser. The health endpoint is
available at `http://localhost:3000/health`.
Build and Run with Docker
Build the image:
``` bash
docker build -t nodejs-demo-app .
```
Run the container:
``` bash
docker run -d -p 3000:3000 --name nodes-test nodejs-demo-app
```
Open `http://localhost:3000` to verify the application.
GitHub Actions Configuration
The workflow is located at:
``` text
.github/workflows/main.yml
```
It is configured to run on pushes to the `main` branch. The workflow
tests the application, builds the Docker image, and pushes it to Docker
Hub.
Required GitHub Secrets
Configure these secrets in the repository's Settings → Secrets and
variables → Actions:
`DOCKERHUB_USERNAME` --- Docker Hub username
`DOCKERHUB_TOKEN` --- Docker Hub access token
Do not commit access tokens or other secrets to the repository.
Docker Hub Image
Repository: `sakthi2300/nodejs-demo-app`
Image tag used by the workflow: `latest-`
Pull the image:
``` bash
docker pull sakthi2300/nodejs-demo-app:latest-
```
Run the published image:
``` bash
docker run -d -p 3000:3000 --name nodes-test sakthi2300/nodejs-demo-app:latest-
```
If the container name `nodes-test` is already in use, choose a different
name or inspect the existing container before removing it.
Repository
GitHub: https://github.com/sakthi2300/nodes-demo-app
What This Project Demonstrates
Automating application tests on code push
Building a Docker image in a CI/CD workflow
Using GitHub Actions secrets for Docker Hub authentication
Publishing a Docker image to Docker Hub
The workflow publishes the image to Docker Hub; it does not deploy a
continuously running application to a cloud server.
