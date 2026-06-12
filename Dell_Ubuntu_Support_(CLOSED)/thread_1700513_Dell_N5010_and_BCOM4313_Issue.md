---
title: "Dell N5010 and BCOM4313 Issue"
date: 2011-03-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by actiononmail on 2011-03-05
Hi All,

I have recently installed Ubuntu 10.04 Edition over my Dell N5010 Laptop.Initially I am unable to connect to my Wireless Router but later on I have installed STA Drivers as well, after reading certain posts over Ubuntu threads.
 Believe me, I even connected to the router for a couple of days.But I dont know what happened now, during connecting to Router it continuously asking me the password for connection with Router, even though I have given right password.Some of the details are as follows:-
output of lshw -C network
-------------------------------------
*-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 70:f1:a1:bf:f8:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:d8:93:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.2 latency=0 multicast=yes
       resources: irq:33 ioport:d000(size=256) memory:d0c10000-d0c10fff(prefetchable) memory:d0c00000-d0c0ffff(prefetchable) memory:fb300000-fb31ffff(prefetchable)
-----------------------------------------------------------------------------------------------------------------------

Please help.

---

