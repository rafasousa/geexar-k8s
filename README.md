# Raspberry Pi Geexar

A cluster of Raspberry Pis is deployed using Ansible and Kubernetes.

<p align="center">
<img src="/images/raspberry-pi-geexar-2020.jpg" alt="Raspberry Pi Geexar" width="70%" /></p>

## Why

This is a project I always wanted to do, and that's when I came a cross the project made by [Jeff Geerling](https://github.com/geerlingguy) the guy is a legend, he is very active in the community and has a project called [Raspberry Pi Dramble](https://github.com/geerlingguy/raspberry-pi-dramble).

Based entirely on this Raspberry Pi Dramble project, I created my Brazilian version [Raspberry Pi Geexar](https://github.com/rafasousa/geexar-raspberry-pi) I forked Jeff's project, removed some things and made it lighter just leaving that you would need for a Kubernetes cluster.

Well that is it if you are interested and want more details doesn't hesitate to open an Issuer or a Pull Request 😉

## Official Project Raspberry Pi Dramble

You can browse more information about _geerlingguy_'s Dramble on [http://www.pidramble.com](http://www.pidramble.com). This site is running on the Raspberry Pi Dramble of Jeff cluster!

## Specs

  - 16+ ARMv7 CPU Cores
  - 5.6 GHz combined compute power
  - 4 GB RAM
  - 128 GB microSD flash-based storage
  - 1 Gbps private network with PoE


## Getting the Pis (and other accessories)

A basic list of components used in constructing:

  - [Raspberry Pis and Accessories](http://www.pidramble.com/wiki/hardware/pis)
  - [Other Necessities](http://www.pidramble.com/wiki/hardware/necessities)
  - [Recommended Extras](http://www.pidramble.com/wiki/hardware/extras)

## Setting up the Pis

The process for setting up all the Raspberry Pis is outlined in the Wiki:

  1. [Prepare the Raspberry Pis for provisioning](http://www.pidramble.com/wiki/setup/prepare)
  1. [Rack the Raspberry Pis](http://www.pidramble.com/wiki/setup/rack)
  1. [Network the Raspberry Pis](http://www.pidramble.com/wiki/setup/network)
  1. [Test the Ansible configuration](http://www.pidramble.com/wiki/setup/test-ansible)
  1. [Provision the Raspberry Pis](http://www.pidramble.com/wiki/setup/provision)
  1. [Deploy Drupal to the Raspberry Pis](http://www.pidramble.com/wiki/setup/deploy-drupal)

#### Adding more nodes

You can add more than four nodes, if you desire; add additional hosts in the same sequence in the following files:

  - `setup/networking/inventory`
  - `setup/networking/vars.yml`
  - `inventory`

If you need to change the IP subnet (default is `10.0.0.x`), make sure to also update `hosts.j2` to use the new subnet so hostnames resolve correctly.

## Local testing

A Vagrantfile is also included for local testing and debugging of the Kubernetes cluster and manifests using [Vagrant](https://www.vagrantup.com). See the [Vagrant README](testing/vagrant/README.md) for more details.

## Initial Setup

Set up Pis networking by assigning a uniform set of IP addresses and hostnames based on Pi MAC addresses.
See the [Networking README](setup/networking/README.md) for more details.

# Others

## Migrate K8s 1.15 to 1.16
https://kubernetes.io/blog/2019/07/18/api-deprecations-in-1-16/

## kubectl proxy
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login

```bash
kubectl proxy

kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')

kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

```
