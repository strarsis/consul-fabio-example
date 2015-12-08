# consul-fabio-example
Example for [fabio](https://github.com/eBay/fabio) + [consul](https://github.com/hashicorp/consul) + [registrator](https://github.com/gliderlabs/registrator) using [docker-compose](https://github.com/docker/compose) ([docker](https://github.com/docker/docker)).


Note
----
registrator is currently commented out (disabled) in docker-compose.yaml.

Usage
-----
Docker + docker-compose have to be installed.

Run consul, registrator, fabio:
````
git clone https://github.com/strarsis/consul-fabio-example
cd consul-fabio-example

docker-compose up -d
````

Run example web node:
````
cd ..
git clone https://github.com/eBay/fabio
cd fabio
export GOPATH=$(pwd)
go get github.com/eBay/fabio
cd ./demo/server
go build server.go

./server -addr 172.17.0.1:5000 -name svc-a -prefix domain.com/foo -consul 127.0.0.1:8500
````

127.0.0.1:8500 for consul web GUI/REST API

127.0.0.1:9998 for fabio web GUI

127.0.0.1:9999 for public facing HTTP
