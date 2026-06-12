---
title: "TrueMobile 1350 Problem (Inspiron 5100)"
date: 2009-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by david.paige on 2009-05-14
I am having a problem with Ubuntu.  I am faced with either getting Ubuntu working, or paying $20 for Presto, which is the only non-Windows distro which has worked out of the box on my 1350 card.

How do I get Ubuntu to recognize my card?  I ran the hardware drivers command, and  it installed (I think) fwcutter, but I don't know how to use it.  Nothing seems to work.  I don't think it's just a matter of my system not doing DHCP (can't figure that out?), and not having the routes and IPs set correctly.  I think it's just not working with my card.

Any ideas so I don't have to buy Presto?

Thanks.

---

### Post by coffeeaddict22 on 2009-05-14
Hi,
A bit more info would help.  
First of all, what version of Ubuntu?  
And is it a standard home network, or is there something unusual about it?
Do you know if the hardware works- has it worked in another OS? 
Have you upgraded or is this a new install?
What 'hardware drivers command' did you run?  There's a few.  Do you mean you went to System/Administration/Hardware Drivers and enabled a driver in there?
Open a terminal and type in the following commands:
```
lshw -C network
ifconfig
uname -a
```
one after the other, and post the results back; enclose them in code tags (that's the # symbol above).
It's not that the terminal is a good way of scaring children; it's just a lot easier to be precise when it's all text based.

---

### Post by david.paige on 2009-05-14
Here is the lshw -C from Presto

```
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ac:39:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:19:29:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11bg

```

and from Ubuntu

```
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ac:39:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:19:29:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: d2:96:b2:6f:1d:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

ifconfig (presto)
```
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ac:39:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:19:29:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: d2:96:b2:6f:1d:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

ifconfig (ubuntu)
```
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ac:39:3e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:19:29:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: d2:96:b2:6f:1d:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

presto works, but not ubuntu

---

### Post by david.paige on 2009-05-15
I almost forgot the unames.  Here they are

Presto
```
Linux presto 2.6.29-presto #1 SMP Tue Mar 24 10:14:02 EDT 2009 i686 GNU/Linux
```

and Ubuntu
```
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

So, long and short, Presto works out of the box, Ubuntu does not.  For the wired network, I had to create static routes and IP addresses to get it to work.  Wireless just plain doesn't want to work.

Thank you in advance for your assistance.

---

### Post by david.paige on 2009-05-15
The 1350 works fine in Windows and Presto.  My home network is an ordinary linksys router.  Both unices are installed under Windows.

---

### Post by coffeeaddict22 on 2009-05-15
OK, a few things to try.  First, sometimes this is that the card is turned off in hardware... if there's a wireless button on your PC, try turning it on.  The older inspirons it was Fn-F2, sometimes it's a separate button or a slider.
If that doesn't work, try ifconfig down and then ifconfig up, just in case.  Finally, reinstall the driver; lsmod to find exactly what it is, (it should be b43, but confirm) then modprobe -r xxxx, then modprobe xxxx

---

### Post by david.paige on 2009-05-15
That didn't work.

I am coming to the conclusion that this just isn't going to work, no matter how much time I put into it.

What about recommendations for non-Broadcom mini-PCI cards?  Should I buy an Atheros-based one?  Or is there a better chipset out there?  What is the most likely to work with Ubuntu and Dell?


Thanks.

---

### Post by coffeeaddict22 on 2009-05-16
Wireless usually works out of the box in Linux now, with a few exceptions.  Part of the problem at present is that the way wireless worked even 6 months ago is significantly different to now (it was a LOT harder.)  Have you looked in System/Administration/Hardware Drivers and enabled the restricted Broadcom driver?

---

### Post by niteshifter on 2009-05-18
> **david.paige said:**
> 
What about recommendations for non-Broadcom mini-PCI cards?  Should I buy an Atheros-based one?  Or is there a better chipset out there?  What is the most likely to work with Ubuntu and Dell?


Intel. Currently using an Intel 3945ABG on Hardy. First started with Edgy and a Intel 2200BG. Have not had a single issue with wireless operation. An occasional hiccup on returning from suspend is all I've encountered with the 3945 card.

---

