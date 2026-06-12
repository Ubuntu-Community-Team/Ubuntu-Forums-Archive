---
title: "Bridging Ethernet"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Descention on 2006-09-07
Hello, I am somewhat new to linux, but im trying to find out if i can set up a network bridge on Ubuntu, like i can in Windows XP.

I've done searches on google, and did not find much help. I asked on #ubuntu irc, but the most i got was that it's possible but no one knew how.

below is current information from lshw ( which i found from [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) )
--------------------------------------------------
root@ubuntu:~# lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth0
       version: 10
       serial: 00:60:67:73:b7:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:c000-c0ff iomemory:dc000000-dc0000ff irq:11
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth1
       version: 10
       serial: 00:48:54:4b:d0:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:c400-c4ff iomemory:dc001000-dc0010ff irq:12
root@ubuntu:~#
--------------------------------------------------


Thank you

---

### Post by Descention on 2006-09-10
alright, i've found the software i need, which is bridge-utils from the synaptec package manager.  I can bridge my two ethernet cards, but if i restart my computer, it does not stay that way.

can anyone help me with this?

---

