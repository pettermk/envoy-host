# Envoy host

This repository defines the infrastructure required to set up a web server
using a combination of envoy proxy, certbot, docker, docker-compose and
github actions to set up a fully automated website where any docker app
can be proxied without worrying about TLS termination

# Certbot

To create a new certbot certificate, run the command

```
sudo certbot --standalone --http-01-port 9000
```

You will be prompted to enter the details of your domain. Follow the steps
and certbot will create a service that listens on port 80 for the certbot
challenge. The http-01-port is the port that certbot will call from externally,
and it is the envoy proxy that forwards these requests to the service running
locally. This makes it possible to renew the certificate while all services
are running.

To renew the certificate, run

```
sudo certbot renew --standalone --http-01-port 9000
```

