---
title: "Running Ubuntu 9.04 I cannot find a driver for my Dell D630 1505 draft wireless card."
date: 2009-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Compuglobalhypermeganet on 2009-05-20
I am sorry if this post already exists, but I can only find drivers for every other wireless card and for older versions like 8.04.  I already searched Dell Ubuntu Wiki forum and never found what I needed.  I also tried searching every combination of the words possible on Google.  Where can I find a driver for my wireless card?  Thank You in advance for any advice.

---

### Post by coffeeaddict22 on 2009-05-21
Hi,
A little more info would help.
The brand name of the card doesn't mean much.  Open a terminal, type in ```
lshw -C network
``` and have a look at the output.  Post it back if you need more help; also, the output from ```
iwconfig
``` would be useful.

---

### Post by Compuglobalhypermeganet on 2009-05-21
> **coffeeaddict22 said:**
> Hi,
A little more info would help.
The brand name of the card doesn't mean much.  Open a terminal, type in ```
lshw -C network
``` and have a look at the output.  Post it back if you need more help; also, the output from ```
iwconfig
``` would be useful.
I typed in the command and this message came up.
>  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb


When I typed in iwconfig, I received no wireless extensions.  I did deactivate the wireless driver that was not doing anything because no open source versions were available for it.  Should I activate it again?

---

### Post by coffeeaddict22 on 2009-05-22
Yes.  Essentially, you haven't got a wireless driver; the system can see your card, but doesn't know how to talk to it.  From what you've said, you're running a Broadcom 4328 card.  
Reinstall the Broadcom driver (System/Hardware drivers), and then if it isn't working type the two commands again.  My system reports back the following: you can see the driver listed down the bottom row.```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0** driverversion=5.10.79.10 ip=192.168.x.x latency=0** module=wl** multicast=yes wireless=IEEE 802.11

```

---

