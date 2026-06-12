---
title: "wireless not working on dell latitude E5400 on ubuntu 9.10 64 bit desktop"
date: 2010-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sureshsamuel on 2010-05-18
Hi,


The wireless on my system stopped working after I installed Ubuntu 9.10 64 bit desktop version, it was working proper with the 9.04 version.

The wired network works proper without any issues

Also, earlier the wireless did work sometimes using the system and with ubuntu 9.10 64 bit.


Not too sure as to the reason for this beahviour.

Has anyone faced this issue previously ?

I have the provided the following details of my system below :

test@Ubuntu-64-Test:~$ sudo lshw -C network
[sudo] password for test: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:5f:df:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:21:9b:df:13:a7
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5756m-v3.11 ip=192.168.210.21 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:30 memory:f68f0000-f68fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
test@Ubuntu-64-Test:~$ 



TIA,

Suresh

---

### Post by mikewhatever on 2010-05-18
It seems to be turned off. Is there a switch or a button to turn the wireless on? You could also try the following command:

sudo ifconfig wlan0 up

---

### Post by sureshsamuel on 2010-05-22
I have upgraded to 10.04 64 bit and still the same problem. Now the wifi light is enabled but wireless does not seem to work.

Also, it is interesting to not that just after the upgrade to 10.04 (after the first reboot) the wireless was working perfect.
However after further reboots the wireless just stopped working and now I remember that it was the same case in 9.10 as well..

No Idea as to what is happening over here


Any ideas to get this working would be great.


TIA

---

### Post by sureshsamuel on 2010-05-22
test@Ubuntu-64-Test:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:5f:df:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:21:9b:df:13:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5756m-v3.11 ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f68f0000-f68fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
test@Ubuntu-64-Test:~$

---

### Post by sureshsamuel on 2010-05-22
now it is working...

Not too sure as to why it never worked.

I basically tried to install the broadcom driver using the ubuntu software update and a tool wicd to manage the wireless connections.

But frankly not too sure how it got working again.

TIA

---

### Post by sureshsamuel on 2010-05-22
it has stopped working again :-(

the system had undergone a filesystem check yesterday after when I restarted and the wireless does not work after that ....

This is a bt irritating ....

any ideas on how I can rectify this ?

TIA

---

