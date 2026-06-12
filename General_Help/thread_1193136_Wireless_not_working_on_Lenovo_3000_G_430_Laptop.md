---
title: "Wireless not working on Lenovo 3000 G 430 Laptop"
date: 2009-06-21
forum: General Help
---

### Post by asamay81 on 2009-06-21
I have a Lenovo 3000 G 430 laptop with Windows XP and Ubuntu 9.04 installed. I am facing problem with the wireless network connection. In XP my laptop wireless is working but in Ubuntu not. In wired connection i am seeing Auto Eth0 driver but no driver is there under wireless. 

For further reference i am attaching two screenshots.

[IMG]http://img190.imageshack.us/img190/1466/screenshotnetworkconnec.png[/IMG]


[IMG]http://img194.imageshack.us/img194/1466/screenshotnetworkconnec.png[/IMG]

waiting eagerly for your help

Thanks

---

### Post by pytheas22 on 2009-06-21
Please open a terminal in Ubuntu, run the following commands and post the output here:
```

lsusb
lspci -nn
lshw -C Network
uname -rm
```

---

### Post by asamay81 on 2009-06-21
Thanks a lot pytheas22 for your reply. here are the terminal outputs

_**lsusb**_
Bus 002 Device 002: ID 064e:a102 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

_**lspci -nn**_
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
05:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
05:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
05:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

_**lshw -C Network**_
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:c0:96:a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:08:08:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=172.16.49.175 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:b4:30:6a:79:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

_**uname -rm**_
2.6.28-11-generic i686

---

### Post by asamay81 on 2009-06-21
what should i have to do now about the wireless issue in my laptop? :(

---

### Post by pytheas22 on 2009-06-21
Ah, it looks like your card is working fine; I think you're just confused about how to connect.  You should be able to connect simply by left-clicking on the NetworkManager icon in the top-right area of your screen.  This will display a list of wireless networks.  To connect, select your network.  It's alright for the 'Wireless' section of network connections to be blank.

If you still have trouble, let me know and I'll post a screenshot showing exactly what to do.

---

### Post by asamay81 on 2009-06-22
it is better pytheas22...please put a screenshot so that the job will be a bit easier to me...so far i could not connect...i am not yet fully accustomed with a linux platform...

---

### Post by pytheas22 on 2009-06-22
Here is a screenshot that will hopefully give you a better idea of where to click.  You just left-click (not right-click) the NetworkManager icon in the upper-right part of your screen.  The icon will probably look like two tiny computer screens by default.  Then you will see the list of networks to connect to.

---

### Post by asamay81 on 2009-06-22
thanks a lot pytheas22....sory for delayed response....i'll take my laptop to the wi-fi zone and let  you know.....

---

### Post by asamay81 on 2009-06-23
i know that asking this is is a foolish game...anyway i know that i am a fool :P

the network icon was there in my panel earlier when i installed my system. latter i removed it thinking that it would not be of any use to me...now while connecting to the wi-fi, i not getting the option from the menu bar...

somebody please tell me how to bring back that small icon (shown by pytheas22) in my panel so that i can connect to wireless....

:(

---

### Post by del_diablo on 2009-06-23
Rightclick on the panel and select "add app" or whatever ut is. Go down and find network manager or whats its name. Not running gnome so i can't say the exact options.

---

### Post by asamay81 on 2009-06-23
yah i got it....i tried in that way only..but overlooked that option :P...


thanks a lot for the replies.....this thread can be closed now :) problem solved :)

---

