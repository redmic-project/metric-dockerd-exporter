# Dockerd exporter

Prometheus exporter for Docker daemon metrics. Inspired by https://github.com/stefanprodan/swarmprom

## Requirements

You must enable Docker `metrics-addr` in all Swarm nodes.

When you are using a Docker version prior to v20.10.0, `experimental` flags must be enabled too.

Edit `/etc/docker/daemon.json` to add these properties:

```json
{
	...
	"experimental": true, #don't set this when Docker version >= 20.10.0
	"metrics-addr": "0.0.0.0:9323"
}
```

Don't forget to restart Docker daemon with `systemctl restart docker` (do it for every Swarm node).
