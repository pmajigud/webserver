"#webserver"

The tast can be split into 3 parts-Pre-requisites,create dockerfile and build image and run time info
1.Pre-requisites:
#Install Docker and its dependencies
#Add user to docker groups
usermod -aG docker $USER
docker info

2.Build artifacts
#Create directory
mkdir myweb
cd myweb
#Create Dockerfile
vi Dockerfile
--
FROM nginx:alpine
COPY index.html /usr/share/nginx/index.html
---
#Create index.html
vi index.html
---
<html>
<body>
Hello Plastiq World!
</body>
</html>
---
#Build your image from Dockerfile
docker build -t myweb .
#List your image
docker images |grep myweb

3. Run & Verify
#Run docker container with your image on port 80 and hostport 80
docker run -it --rm -p 80:80 myweb
#Check if container is running at 8080
curl localhost:8080
Point your browser to http://localhost:8080
