---
title: "Wired network has an intermittent connection"
date: 2012-08-12
forum: Desktop Environments
---

### Post by middlechild on 2012-08-12
Installed clean tonight the 64Bit Desktop 12.04 system. The network connection works intermittently meaning web sites .  The drivers are from Ubuntu, not proprietary.   All available updates are installed already.  The error is:

"Firefox can't find the server at www.reddit.com."

Suggestions?  Thanks.

cat /etc/network/interfaces
auto lo
iface lo inet loopback

Wired network:
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:1c:c0:fe:4b:32
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:d000(size=256) memory:d0114000-d0114fff memory:d0110000-d0113fff memory:d0100000-d010ffff

---

### Post by middlechild on 2012-08-13
I have read other posts about disabling dns resolve to work around this issue. Is the resolver going to be fixed anytime soon?  I have a hard time believing that basic IP functionality is broken only in my environment and not everyone is having issues with this. Seems pretty basic but perhaps I am missing something?

---

