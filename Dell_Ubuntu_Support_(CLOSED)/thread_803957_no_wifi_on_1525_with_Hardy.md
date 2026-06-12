---
title: "no wifi on 1525 with Hardy"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aggiemarine07 on 2008-05-22
Howdy!

I have a brand new Inspiron 1525 and I can not get the wireless to work properly on it at all. I have tried just about every technique from ndiswrapper (with the B43legacy driver bmwl5.inf) to fwcutter (with the same driver) to get this working. When I was using 7.10 it worked flawlessly but ever since I have upgraded to 8.04 the wireless has never worked for more than a few hours and now it is not connecting at all.

I know for sure that it works because I can piggy-back on someone else's unsecure wireless and connect just fine. However whenever I try to connect to my wireless router (Belkin wireless-g f5d7230-4 router) it only gets one green dot, times out, and then it tries to connect to the open wireless connection of my neighbors.

Here is the output of lshw -C network

 description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:44:72:33:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.1.102 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



Is there anyone out there that can help me with this? Thanks!

---

