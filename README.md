# Laravel development with Docker
Development Laravel use Docker

##### 1. Pull images
`docker pull pnlinh/app:latest`

`docker pull pnlinh/mysql:latest`
##### 2. Create network
`docker network create appnet`

##### 3. Create volume
`docker volume create mydata`

##### 4. Run container and connect it
```
docker run --name=app --network=appnet -d --rm -p 80:80 -v $(pwd)/application:/var/www/html pnlinh/app:latest

docker run --rm -d \
--name=mysql \
--network=appnet \
-v dbdata:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=homestead \
-e MYSQL_USER=homestead \
-e MYSQL_USER_PASSWORD=secret \
mysql:5.7
```

##### 5. Config database
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=root
DB_PASSWORD=root
```

##### 6. Run application
`docker exec -it -w /var/www/html app php artisan migrate`

Browser to: `http://localhost`
