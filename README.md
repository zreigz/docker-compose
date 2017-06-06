# Docker Compose

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a Compose file to configure your application’s services. Then, using a single command, you create and start all the services from your configuration. To learn more about all the features of Compose see the list of features.

Compose is great for development, testing, and staging environments, as well as CI workflows. 

## Install Docker Compose
Download Compose version 1.13.0, the command is:

```
$ sudo su
# curl -L https://github.com/docker/compose/releases/download/1.13.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
# exit
```

Apply executable permissions to the binary:

```
$ sudo chmod +x /usr/local/bin/docker-compose

```

## Installing Thingsboard using Docker


Download the following files from thingsboard repo:
* docker-compose.yml - main docker-compose file.
* docker-compose.random.yml - overwrite docker-compose file with thirdparty ports configuration.
* .env - main env file that contains default location of cassandra data folder.
* thingsboard.env - default thingsboard environment variables.
* thingsboard-db-schema.env - default db-schema environment variables.

```
curl -L https://raw.githubusercontent.com/thingsboard/thingsboard/release-1.2/docker/docker-compose.yml > docker-compose.yml
curl -L https://raw.githubusercontent.com/thingsboard/thingsboard/release-1.2/docker/docker-compose.random.yml > docker-compose.random.yml
curl -L https://raw.githubusercontent.com/thingsboard/thingsboard/release-1.2/docker/.env > .env
curl -L https://raw.githubusercontent.com/thingsboard/thingsboard/release-1.2/docker/thingsboard.env > thingsboard.env
curl -L https://raw.githubusercontent.com/thingsboard/thingsboard/release-1.2/docker/thingsboard-db-schema.env > thingsboard-db-schema.env
```

Create cassandra data directory:

```
$ mkdir ~/cassandra_volume

```


Update `.env` file and change cassandra data folder for your home directory

```
CASSANDRA_DATA_DIR=/home/<user>/cassandra_volume
```


```
$ nano .env

```



Execute docker-compose command to start Thingsboard node and all thirdparty components

```
sudo docker-compose -f docker-compose.yml -f docker-compose.random.yml up -d
```

Once started, you will be able to open Web UI using following link:

```
http://localhost:8080/
```

Login as a tenant administrator

The first step is to login to administration Web UI.

If you are using local Thingsboard installation you can login to administration Web UI using default account:

```
    Username: tenant@thingsboard.org
    Password: tenant
```

More info (here)[https://thingsboard.io/docs/getting-started-guides/helloworld/]
