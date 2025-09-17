# build image
docekr build -t <image_name>:<tag> -f <image_path>
docker build -t docker-basic:latest -f deployment/docker/app/Dockerfile .

# run container
docker run -d -p <external_port>:<internal_port> --name <container_name> <image_name>
docker run -d -p 8080:8080 --name my-app docker-basic:latest # general
docker run -d -p 8080:8080 --env-file deployment/docker/app/.env --name my-app docker-basic:latest # env file
docker run -d -p 8080:8080 -e PORT=9000 -e APP_NAME="Custom App" --name my-app docker-basic:latest # env variables

# command check 
docker ps
docker container list
docker image list
docker network list
docker volume list

# remove 
docker stop <container>
docker rm <container>
docker rmi <image_name>
docker network rm <network_name>
docker volumn rm <volumn_name>

# prune 
docker container prune
docker image prune
docker network prune
docker volume prune
docker system prune