
# Dcoker stack Keycloak

Init docker Swarm

```
docker swarm init
```

create network

```
docker network create \
  --driver=overlay \
  --scope=swarm, \
  --subnet=172.24.10.0/24 \
  --gateway=172.24.10.1 \
  --attachable \
  app-network
```

create directory cert & providers

```
mkdir cert
mkdir providers
```

create certificate
```
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 3650 -nodes -subj "/C=XX/ST=StateName/L=CityName/O=CompanyName/OU=CompanySectionName/CN=CommonNameOrHostname"

mv cert.pem cert/

mv key.pem cert/
```

to deploy 

```
docker stack deploy -c stack.yml keycloak
```

to destroy
```
docker stack rm keycloak
```
