---
title: "Ethernet connected, but not able to access the internet"
date: 2010-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Biohmmwv on 2010-08-17
I am asking for some help with a weird problem.
I have a Dell 1721 laptop running Ubuntu 9.04 and 10.04. Internet is working fine in 10.04. However, in 3.04 the ethernet was working fine, and then stopped working right as Firefox was restoring the tabs after a reboot.
I am using Wicd for the network manager, and according to the Network tools the computer is sending and receiving packets. I tried pinging Google but get an error message, I'll have to reboot to get the message again. I am having other trouble with 10.04, and that is why I would like to stick with 9.04 for the time being. 

Here is the message I received when I put the command "dmesg | grep eth" in: 
 
[    1.650617] Driver 'sd' needs updating - please use bus_type methods 
[    1.650625] Driver 'sr' needs updating - please use bus_type methods 
[   11.359999] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.91.9 
[   11.563053] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:89:cc:bf 
[   11.568932] udev: renamed network interface eth0 to eth1 
[   11.614704] udev: renamed network interface eth1_rename to eth0 
[   17.839573] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   20.805173] b44: eth0: Link is up at 100 Mbps, full duplex. 
[   20.805177] b44: eth0: Flow control is off for TX and off for RX. 
[   20.805470] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   24.476214] b44: eth0: powering down PHY 
[   24.683716] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   27.596026] eth1: no IPv6 routers present 
[   27.804184] b44: eth0: Link is up at 100 Mbps, full duplex. 
[   27.804188] b44: eth0: Flow control is off for TX and off for RX. 
[   27.804522] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   38.588026] eth0: no IPv6 routers present 
[  464.468234] b44: eth0: powering down PHY 
[  464.533843] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  467.988203] b44: eth0: Link is up at 100 Mbps, full duplex. 
[  467.988212] b44: eth0: Flow control is off for TX and off for RX. 
[  467.988808] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[  478.256031] eth0: no IPv6 routers present 

For  "sudo ifup eth0 output" 
ifup: interface eth0 already configured 
Ignoring unknown interface output=output.

Why is it that the computer can send and receive packets, but can not get onto the net? I was unable to find a solution to this on my own. I probably was not using the right search terms.

---

### Post by lovinglinux on 2010-08-18
See ipv6 at [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

