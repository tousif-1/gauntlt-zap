# Gauntlt with ZAP and Arachni for Docker
This repo is intended for hosting a handful of scripts for security testing based on [James Wickett's security testing class](https://github.com/wickett/security-testing-class), and [dockerized owasp-zap for CI/CD by Stephen Donner](https://github.com/stephendonner/docker-zap)

## How it works
The Gauntlt container is purposely made to get started with security testing with Gauntlt.

- Arachni, nikto, dirb, sqlmap, nmap, owasp-zap (zap-cli, and zapr are included) are installed inside the container as a basic set of attacking tools
- Gauntlt is installed and is set as the entrypoint
- You can run `make path` for including `gauntlt-docker`and other scripts into your path

You can also run your attacks using Arachni or ZAP outside Gauntlt. There are two ad-hoc scripts for doing that you can use and modify:

- ``zap-docker <target-url>``
- ``arachni-docker <target-url>``

## Setup

1. Clone this repo
  ```
  git clone https://github.com/devopstf/gauntlt-zap
  ```

2. Build the docker container

  ```
  $ cd /path/to/cloned/repo/gauntlt-docker
  $ make build
  ```

3. Copy binary stub to your $PATH (like `/usr/local/bin`)
  ```
  $ make path
  ```

4. Test it out with a `gauntlt-docker --help`

5. You can get interactive access to the container (with current path bind mounted to ``/working``) to test attack tools installed
  ```
  $ make interactive
  ```

6. You can set your target URL into the config file for Cucumber, located at ``config/cucumber.yml``, using the following command:
```
$ gauntlt-target <target-url>
```
