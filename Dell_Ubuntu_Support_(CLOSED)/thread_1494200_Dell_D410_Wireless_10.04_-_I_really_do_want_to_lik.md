---
title: "Dell D410 Wireless 10.04 - I really do want to like Ubuntu"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spuudercat on 2010-05-26
OK so heres the thing I never was a Linux bunny, and decided never to darken my door with it... but.... one day it happened and I was a happy low level Ubuntu confused user enjoying all the thrills and spills it had to offer, in fact I still am but :-

Why is there such a bother with the wireless on the Dell machines? Version 9 slowed down the machine to a virtual stop and using it to stream video or get a file any more than 2MB was painful. Then came version 10.04 and I was overjoyed to see after the install the wireless issues that I'd read 5 zillion posts on how to fix it were all fixed, I was in Bliss..

So why after week do they reappear? Why did my system suddenly half way through the day not want to see the AP any more? And now I have managed to get the thing to see it its chuffing slow again??@@>@?P:{}:>>>:@?

Heres a dump of the Wireless, if anyone out there has any idea then please help, I cant go down the route of reading all the docs again on how to speed it up... I will... revert to Windows Gulp!

any help is mucho appreciated

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:6f:05:f5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:79:b7:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.13 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

