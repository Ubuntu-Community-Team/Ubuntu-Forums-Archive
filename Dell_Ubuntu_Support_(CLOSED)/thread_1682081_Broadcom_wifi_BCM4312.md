---
title: "Broadcom wifi BCM4312"
date: 2011-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PouletEnFeu on 2011-02-03
I'm having pretty much the same problem but the lshw -C network thing looks a little different: 
[HTML]  jordan@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:00:9b:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A ip=192.168.1.13 latency=0 multicast=yes
       resources: irq:45 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1efc000-f1efffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:5f:47:a8:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-25-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
               [/HTML] 
Hopefully that will help you to help us

---

### Post by ugm6hr on 2011-02-05
> **PouletEnFeu said:**
> Hopefully that will help you to help us
Your card is completely different, but your solution is easier:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)
If you have any further feedback - post in a new thread to avoid confusing the original posters query.

---

