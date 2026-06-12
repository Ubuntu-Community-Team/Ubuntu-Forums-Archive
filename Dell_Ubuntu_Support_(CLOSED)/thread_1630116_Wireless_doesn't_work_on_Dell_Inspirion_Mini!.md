---
title: "Wireless doesn't work on Dell Inspirion Mini!"
date: 2010-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MacintoshLover on 2010-11-24
Help! I have had Ubuntu 10.10 for a month and my wireless drivers stopped working suddenly. I had to install a proprietary driver to get it to work the first time, and I am using Ethernet to connect. Also, is  it sudo lshw-C? Please Help!!!:sad::confused:

I fixed it! I entered the commands```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```and it worked. The driver worked

---

### Post by fjgaude on 2010-11-26
Okay, this will do it:

```
sudo lshw -c lan
```

Let us know if you need anything else.

---

### Post by MacintoshLover on 2010-11-27
Results of sudo lshw -c lan :

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:f1:50:69
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 90:4c:e5:43:f0:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-23-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
```
Please Help!!! 
PS thanks fjguade!

---

### Post by ugm6hr on 2010-11-27
I'd suggest trying the wl driver (STA).
I originally thought that the proprietary driver worked better, but it was very unreliable.

---

