
# We are creating Redis cluster with 3 nodes, 3 master with no slaves

**Step1: Create the container**

    docker-compose up -d

**Step 2: Get the ip address of redis nodes**
   
    docker inspect redis-cluster_redis-cluster

**Step 3: Get network names**

    docker network ls

**Step 4: Create cluster** 

In the container, you can run 

      redis-cli --cluster create <ip of redisnode-1>:6379 <ip of redisnode-2>:6379 <ip of redisnode-3>:6379 --cluster-replicas 0

Directly run in your terminal
 
    docker-compose exec redis-1 redis-cli --cluster create 172.28.0.2:6379 172.28.0.3:6379 172.28.0.4:6379 --cluster-replicas 0

use internal container ports

**Step 6: Check the cluster status**

    redis-cli -h <ip of any node> -p <port> CLUSTER NODES
