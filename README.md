# two-docker-compose-on-primary-nginx-proxy

I run this command to set **nginx-proxy** as primary proxy on my real VPS centos 8 server :



```console
docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock:ro nginxproxy/nginx-proxy
```


<br><br>


I want when visit normal real URl : 

www.real-domain-1.com point to docker container ID xxxxxxx1

www.real-domain-2.com point to docker container ID xxxxxxx2

<br><br>


I run this command for each directory: 

(/var/www/html/www.real-domain-1.com/) and (/var/www/html/www.real-domain-2.com/)

```console
docker-compose up -d --build
```

> you can find same code as https://github.com/performautodev/two-docker-compose-on-primary-nginx-proxy/tree/main/

Successfully built 8a3eac9ed4e5

> Dosen't work

<br><br>


But if I run eatch container speatrely works :


```console
docker images
```

```
REPOSITORY              TAG       IMAGE ID       CREATED          SIZE
wwwXXX1_react-web-app   latest    507556bce57a   2 hours ago      134MB
wwwXXX2_react-web-app   latest    8a3eac9ed4e5   2 hours ago      134MB
```


```console
docker run -d -e VIRTUAL_HOST=www.real-domain-1.com wwwXXX1_react-web-app
```


```console
docker run -d -e VIRTUAL_HOST=www.real-domain-2.com wwwXXX2_react-web-app
```

