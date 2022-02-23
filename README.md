# Perfect World Server in Microservices
Run every perfect world server subsystems in each container with separate MySQL server. This to archive better scalability for each subsystems.

### Description
- server version 1.5.5 build 2567
- simple user registration
- all subsystems is running on Ubuntu 18.04 images

You can run individual subsystem, since it't using different images
- ossperfectworld/perfect-world-authd
- ossperfectworld/perfect-world-gacd
- ossperfectworld/perfect-world-gamed
- ossperfectworld/perfect-world-gamedbd
- ossperfectworld/perfect-world-gdeliveryd
- ossperfectworld/perfect-world-gfactiond
- ossperfectworld/perfect-world-glinkd
- ossperfectworld/perfect-world-logservice
- ossperfectworld/perfect-world-uniquenamed
### Installation
**It's doesn't care about the operating system, as long as it can run docker & docker-compose, should be fine! tested in Ubuntu 18.04**

- clone this repository
```
git clone https://github.com/oss-perfectworld/perfectworld.git
```
- edit docker-compose.yaml, change `{PUBLIC_IP}` with your server public IP
```
    ports:
    - "{PUBLIC_IP}:29000:29000"
```
- run all services
```
make up-perfectworld
```

### Developing
TBD

### Future Feature
currently, it's not support `pwAdmin` since `pwAdmin` required modifiying & executing to each subsystems. This is not possible in microservices, since we are running each subsystems in different container.

### Troubleshooting
#### Server Network Error
try to restart authd container by running this command
```
docker stop perfectworld-authd
docker start perfectworld-authd
```
