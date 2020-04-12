# Vox Pupuli Build Containers

This repository contains the Docker build files for our build containers used to build RPM and DEB packages.

## Building

### Clone and build the base containers

Ubuntu 18.04 example:
```
$ git clone git@github.com/voxpupuli/vox_containers.git
$ cd vox_containers/
$ docker build -f build/distros/ubuntu/Dockerfile.bionic -t voxpupuli/ubuntu:bionic .
```

The following distros are currently available for base containers:

* Ubuntu 16.04 Xenial (Will be EoL by Apr 2021)
* Ubuntu 18.04 Bionic
* Enterprise Linux 7
* Enterprise Linux 8
* Debian 9 Stretch
* Debian 10 Buster

Coming TBD:
* Ubuntu 20.04 Focal
* OpenSUSE/SLES (Looking for contributors)

### build the builder containers

These are the containers actually used to build the packages. We have 2 of them:

* One for RPMs
* One for DEBs

To build the builder container, you need to add the `--build-arg` option. For example, to build an Ubuntu Bionic image for building Bionic DEB packages:

```shell
docker --build-arg=DISTRO=ubuntu --build-arg=VERSION=bionic -t voxpupuli/builder:bionic -f build/builders/Dockerfile.builder.apt .
```
