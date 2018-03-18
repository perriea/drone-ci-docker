# Drone on docker-compose/Swarm

This repository contains a minimal example of Drone running within [docker-compose](https://docs.docker.com/compose/overview/) or Swarm. This is a quick and easy way to experiment with Drone.
  
## Dependencies

We recommend:

* [docker Engine](https://docs.docker.com/engine/installation/) >= 1.13.0
* [docker-compose](https://docs.docker.com/compose/install/) >= 1.18.0

## How this works

docker-compose reads the `docker-compose.yml` file and spins up three containers:

* Drone Server
* Drone Agent
* MariaDB/MySQL

The former serves the web UI and responds to webhooks. The Drone Server's port 80 is mapped to the host and bound on 0.0.0.0. You'll need to expose this port to Github for it to be able to receive push/PR/tag webhooks.

## Quickstart

* Add a Drone OAuth application in your [Github settings](https://github.com/settings/profile). This can be done on your account, or on any organization that you have sufficient permissions to. Use something like this as your authorization callback url: `http://drone.mycompany.com/authorize`
* Open `docker-compose.yml`. Search for "`CHANGEME`" and change the values as directed. Make sure to substitute your Github OAuth application credentials.
* run `docker-compose up -d`
* Make port 80 on the machine you are running this on open to the internet.
* Point your browser at `http://drone.mycompany.com`.

## Tips

* This demo does not include HTTPS, which is generally a good idea for production installs.
* You can :
    * scale the number of agents servicing builds like this: `docker-compose scale drone-agent=3`,
    * plug CDN some **Cloudflare** ou ** AWS CloudFront**. This solution makes it possible to put the access in HTTPS easily and quickly.

## Need help

If you have questions, post them to our [Help!](https://discourse.drone.io) category on the Drone Discussion site. If you'd like a more realtime option, visit our [Gitter room](https://gitter.im/drone/drone).

## Contributions

If you have anything to add or improve, please don't hesitate to send
pull requests.

## Licence

Licence [MIT](http://opensource.org/licenses/mit-license.php)   
Developed by [Aurelien Perrier](http://about.me/perriea)