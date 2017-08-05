# wakanda-docker
Docker configuration for all repositories

On wakanda-docker directory do:
Step 1: docker run --detach --name consul --hostname consul-server-1 progrium/consul -server -bootstrap -ui-dir /ui
Step 2: CONSUL_IP=$(docker inspect -f '{{ .NetworkSettings.IPAddress }}' consul)
Step 3: docker build -t redis-statistic-receiver redis-statistic-receiver
Step 4: docker run --detach --name redis-statistic-receiver \--hostname redis-statistic-receiver-1 \--env CONSUL_HOST=$CONSUL_IP redis-statistic-receiver 
Step 5: git clone https://github.com/wakanda-cloud/wakanda-statistic-receiver wakanda-statistic-receiver
Step 6: docker build -t wakanda-statistic-receiver wakanda-statistic-receiver
Step 7: docker run --detach --name wakanda-statistic-receiver \--hostname wakanda-statistic-receiver-1 \--env CONSUL_HOST=$CONSUL_IP wakanda-statistic-receiver 

In developing...

