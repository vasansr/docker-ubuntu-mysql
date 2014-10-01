#docker-ubuntu-mysql
Dedicated mysql container, intended for exposure to another container.
 
## About

This mysql container is based on ubuntu:trusty, and has the following in addition:

* mysql-server
* Listens on 0.0.0.0 instead of the default 127.0.0.1
* Port 3306 is exposed, in case you are not linking containers
* Allows for a root password to be set when run for the first time

## Example

### Running

Simple, not exposed:

```shell
docker run -d --name="mysql-run" \
    -e "MYSQL_PASSWORD=password" \
    vasansr/ubuntu-mysql
```

Exposed: 

```shell
docker run -d --name="mysql-run" \
    -e "MYSQL_PASSWORD=password" \
    -p 3306:3306 \
    vasansr/ubuntu-mysql
```

Explanation:

* -d : Run daemonized
* --name : The name of the container
* -e MYSQL_PASSWORD : To set the root password for connecting from other containers/hosts. Change password to the password that you want to set. Use a strong password if you are exposing the container using -p
* -p : expose port 3306 as port 3306 on the host
* vasansr/ubuntu-mysql : The name of the repository	

