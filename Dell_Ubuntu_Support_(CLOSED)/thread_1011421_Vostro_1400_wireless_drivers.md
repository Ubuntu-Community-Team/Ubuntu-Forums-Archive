---
title: "Vostro 1400 wireless drivers"
date: 2008-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a5k3r on 2008-12-14
Hi,

I am new to Linux and tried to fix the wireless driver issue for my Vostro 1400. I looked up online and followed a lot of instructions from the forums. But none worked. So I decided to start a new thread. 

Anyway here are the details of my comp:

```
aravind@a5k3r-DELL:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:fd:c5:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=172.24.201.174 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:e2:d9:1b:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

aravind@a5k3r-DELL:~$ lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```


Any help would be really appreciated. Thanks in advance.

---

### Post by user_linux08 on 2008-12-15
I use the B43-Fwcutter driver.it seems to work fine. you can download it with synoptics.

---

### Post by deadbeef on 2008-12-15
...without a working connection on the laptop, how are you supposed to use synaptics?

I don't mean to sound like a wiseacre, but I want/need to know if it's possible.

---

### Post by user_linux08 on 2008-12-16
no you don't sound "wiseguy". It happnes to more users then one admits.
I am not sure if the B43-fwcutter comes with the Intrepid CD or not. However, there is a way to get around it.
If you have a cable/wireless Router, then you could run an RJ-45 cable to the dell, just long enough to download and install the wireless drivers, then cut go wireless. 
That is my solution (anyway)

---

### Post by a5k3r on 2008-12-17
Thanks for the info. I managed to get it working.

I just had to type 
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

and it works. 

Found the details at:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

