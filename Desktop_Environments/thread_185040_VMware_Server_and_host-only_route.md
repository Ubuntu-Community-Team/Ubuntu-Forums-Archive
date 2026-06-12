---
title: "VMware Server and host-only route"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Swad on 2006-05-31
I am setting up a VMware server with the host as Ubuntu 5.10.  Everything has been setup and is for the most part working fantastically.  I am aiming to setup a host-only network that will be routed into our private lan at work.  This will keep the virtual environment on its own subnet but with connectivity to the LAN.  That said, here is my current routing table on the host machine:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.163.0   *               255.255.255.0   U     0      0        0 vmnet2
localnet        *               255.255.255.0   U     0      0        0 eth1
192.168.79.0    *               255.255.255.0   U     0      0        0 vmnet8
172.16.126.0    *               255.255.255.0   U     0      0        0 vmnet1
default         192.168.0.11    0.0.0.0         UG    0      0        0 eth1

```

vmnet1 and vmnet2 are host-only while vmnet8 is NAT.  How would I setup a proper route to where vmnet2 can talk to lan traffic on the 192.168.0.0/24 subnet?  I'll be honest that I'm totally green at setting up routes, so someone will have to spell it out for me  ;)

Thanks for any help tying up this last end with my VMware setup.

---

