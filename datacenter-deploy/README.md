## Overview

Deploy a Consul datacenter containing a single server and clients, including DNS support.

## Prerequisites

- Docker
- Docker Compose (part of Docker release)
- git (apt install git, snap install git)

## Deployment procedure

1. Clone [learn-consul-docker](https://github.com/hashicorp/learn-consul-docker) repository (`git clone https://github.com/hashicorp/learn-consul-docker`)
2. Navigate to this directory (`cd learn-consul-docker`).
3. Go to 'datacenter-deploy-dns' directory (`cd datacenter-deploy-dns`)
4. Update the DNS resolver on the host `nano /etc/resolv.conf`, adding the following two lines after the existing name server:

`nameserver 10.5.0.2  #our new Consul DNS server`

`nameserver 1.1.1.1   #global DNS server`

5. Stop the local DNS server by typing `systemctl stop systemd-resolved`
6. Type `docker compose up -d` to build the Consul environment
7. Confirm DNS is working by running `ping consul.service.consul`

## Testing procedure

1. Navigate to [http://localhost:8500/ui](http://localhost:8500/ui/) on your local browser.
2. Explore UI.
3. Explore [Get Started](https://developer.hashicorp.com/consul/tutorials/docker/docker-compose-datacenter) collection.

## Additional information

- [https://learn.hashicorp.com/collections/consul/docker](https://learn.hashicorp.com/collections/consul/docker)
- [https://learn.hashicorp.com/tutorials/consul/get-started](https://learn.hashicorp.com/tutorials/consul/get-started)
