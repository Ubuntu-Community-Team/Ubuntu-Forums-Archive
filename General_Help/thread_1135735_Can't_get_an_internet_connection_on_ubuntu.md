---
title: "Can't get an internet connection on ubuntu"
date: 2009-04-24
forum: General Help
---

### Post by RileyRandom on 2009-04-24
okay since this is my first post i will introduce my self. Hello, i am RileyRandom (::guitar:
here is my problem; i have a perfectly fine internet connection on vista. but when i boot up ubuntu i can not find my router, i have tried to type it in manually and it makes a sets up a connection thing, but i can't connect to it. 

now what could this be? if you have an answer please provide with a lot of info. this is my VERY first time using ubuntu and i know VERY little about it. but i do know quite a lot about vista.

if you need any information to better help me with this, just tell me how to get that information and i will give it to you. 

now please help?


edit: i can connect with Ethernet cable. but i can get a wireless connection through my router

---

### Post by snickity on 2009-04-24
Hi Riley,

Since you mentioned that you were fairly new to Ubuntu are you familiar with accessing the Terminal. You can access the terminal by going to -- Applications>>Accessories>>Terminal

What version of Ubuntu did you install 8.04, 8.10 or 9.04? (You can got System>>About Ubuntu and then click on "Version & Release Numbers"

You said you typed your network info manually, did you do this using the the Network Manager Applet(icon on the top right with two computers)? Were you able to see the name of your wireless network?

---

### Post by RileyRandom on 2009-04-24
i know how to use the terminal and i am using ubuntu 9.04

---

### Post by snickity on 2009-04-24
If your network manager doesn't show any networks listed then you would have to go to the terminal and to get more info. 
 
Use the following command in terminal 

sudo lshw -C network

What that will do is list hardware. And you will see if the wireless card is detected. Go ahead and post the output in the forum.

---

### Post by RileyRandom on 2009-04-25
> **snickity said:**
> If your network manager doesn't show any networks listed then you would have to go to the terminal and to get more info. 
 
Use the following command in terminal 

sudo lshw -C network

What that will do is list hardware. And you will see if the wireless card is detected. Go ahead and post the output in the forum.

here is everything that comes up in the terminal.


riley@ubuntu:~$ 
riley@ubuntu:~$ sudo lshw -C network
[sudo] password for riley: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b0:c1:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:67:c9:50:50:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
riley@ubuntu:~$

---

