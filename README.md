docker-phabricator
==================
A docker composition for Phabricator :
- One container used by mysql, see https://github.com/yesnault/docker-phabricator/tree/master/database
- One container used by apache (phabricator)

Run with image from hub.docker.com
----
Run a mysql container :
```
docker run -d --name phabricator-db yesnault/docker-phabricator-mysql
```

Run phabricator :
```
docker run -d --name phabricator-main -p 8081:80 --link phabricator-db:database --restart always yesnault/docker-phabricator
```
If you wish to set a ServerName for the apache virtual host, use the APACHE_SERVER_NAME environment variable :
```
docker run -d -e "APACHE_SERVER_NAME=your.domain.com" \
--name phabricator-main -p 8081:80 \
--link phabricator-db:database \
--restart always \
robertofilho/phabricator
```

Go to http://localhost:8081

Running on OSX
-------

Requires

  * boot2docker

  * docker

From a terminal, execute:

```
docker-compose up
```

and then execute

```
boot2docker ip
```

Then open up a browser and navigate to

```
http://{boot2docker ip}:8081
```
