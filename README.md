# ansible-role-docker-teamspeak
This role configures and starts docker-composed based teamspeak servers.

## Defaults

### Server definition
Server can be defined in a list. There is a default server instance configured to start:

```yaml
# a default server instance
docker_teamspeak_servers:
  - server: default
    voice_server_port: 9987
    server_query_port: 10077
    file_transfer_port: 30033
    database_password: Te4mspeak3
    restart: always
    stopped: no
```
- The port parameters are the host ports mapped with container ones.
- See https://docs.docker.com/compose/compose-file/#restart for informations about restart parameter.

### Folder structure

```yaml
# basedir where the data and docker-compose files are stored
docker_teamspeak_base_dir: /opt/teamspeak
```
The role writes for every server in the list a folder structure as follows:

```
/opt/teamspeak/
├── default/
│   ├── ts3server               # data volume mounted in ts3server container
│   ├── database                # data colume mounted in mariadb container
│   └── docker-compose.yml
├── .../
│   ├── ts3server
│   ├── database
│   └── docker-compose.yml 
├── .../
```

### Docker specific

```yaml
# always pull the images before starting
docker_teamspeak_pull: yes
```
