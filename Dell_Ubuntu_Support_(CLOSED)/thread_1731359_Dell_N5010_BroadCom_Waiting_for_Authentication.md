---
title: "Dell N5010 BroadCom Waiting for Authentication"
date: 2011-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by actiononmail on 2011-04-17
Hi all,

I have installed Kubuntu 10.04 Edition over my Dell Laptop N5010 Model.As expected, some of thing does not work seamlessly.But most important of them is that, there is no Wireless Connectivity from my Laptop to Beetel Wireless Router.

After some dig up I have found that Broadcom STA wireless Drivers are not installed. So I have installed them, after that KDE Network Manager shows up the Identified Wireless Network.Please see following configure snapshot.

[http://img848.imageshack.us/img848/624/wirelessconf.png](http://img848.imageshack.us/img848/624/wirelessconf.png)

After this the system remains in connecting state, but does not connect it at all.Same configuration works for Windows 7 OS. Please can you guide me for this issue.I am posting output of lshw as a reference.

```

WARNING: you should run this program as super-user.
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
       resources: irq:34 ioport:d000(size=256) memory:d0c10000-d0c10fff(prefetchable) memory:d0c00000-d0c0ffff(prefetchable) memory:fb300000-fb31ffff(prefetchable)


```

---

