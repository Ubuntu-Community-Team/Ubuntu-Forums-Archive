---
title: "no wifi after upgrade to 12.04 on dell studio xps 1340"
date: 2012-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yaron86 on 2012-06-19
hi, i just upgrade to ubuntu 12.04 LTS and i see there is no WIFI, even not my SSID.. nothing..
i have DELL Studio XPS 1340 laptop

why there is no wifi?? 
please help, i'm now with a network cable only, but no WIFI..

---

### Post by nothingspecial on 2012-06-19
Please post your wifi card details

```
sudo lshw -C network
```

---

### Post by yaron86 on 2012-06-19
> **nothingspecial said:**
> Please post your wifi card details

```
sudo lshw -C network
```

```
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:ee:93:40
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.198 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff
yach@yach-laptop:~$ 

```

---

### Post by westie457 on 2012-06-19
Hi take a look at this page. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It has various ways for you to install the Broadcom STA driver that you need.

---

### Post by yaron86 on 2012-06-19
> **westie457 said:**
> Hi take a look at this page. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It has various ways for you to install the Broadcom STA driver that you need.

i installed bcmwl-kernel-source package and install from terminal, and it said:

```
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  kdesudo update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
yach@yach-laptop:~$ 

```

and then went to additional drivers and tried to activate the broadcom STA wireless driver
and it says: "Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log"

please direct me what to do, im kind of new in ubuntu

---

### Post by nothingspecial on 2012-06-19
Have a look at this recent post.

[http://ubuntuforums.org/showthread.php?t=2005942](http://ubuntuforums.org/showthread.php?t=2005942)

---

### Post by yaron86 on 2012-06-19
> **nothingspecial said:**
> Have a look at this recent post.

[http://ubuntuforums.org/showthread.php?t=2005942](http://ubuntuforums.org/showthread.php?t=2005942)

tried it, still no wifi :\
---Edit---
it worked! i restarted my computer and tried to activate the driver in additional drivers and it worked!!! thanks a lot !!!!

---

