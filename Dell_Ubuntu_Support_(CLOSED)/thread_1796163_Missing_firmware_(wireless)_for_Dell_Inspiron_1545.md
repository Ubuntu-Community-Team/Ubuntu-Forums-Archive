---
title: "Missing firmware (wireless) for Dell Inspiron 1545 running Ubuntu."
date: 2011-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by egdisco on 2011-07-03
Hi,
I have seen other threads, and have tried to do it manually by reading the threads through but I can't solve this.

I have a Dell Inspiron 1545, with Windows 7 installed. I have dual-booted it with Ubuntu but the wireless won't work due to it not having the right firmware.

I need help, as Ubuntu looks really good but I will (of course) need the internet on it. I can't connect it to my router via Ethernet cable as I have broken the port on my laptop (stupid thing to do, wish I hadn't).

Thanks for the help,
George.

---

### Post by park_ridge_dave on 2011-07-03
Goerge,

I am relatively new here (I joined yesterday). I had a similar problem. Do you know which version wifi "card" you have? Mine was a Broadcom 4311 and if you read my post you will see how I solved my firmware issue.

Here is the link to my post (it should be about 10 "down" from this post).

Here is the link

[http://ubuntuforums.org/showthread.php?t=1795570](http://ubuntuforums.org/showthread.php?t=1795570)

Make sure that you have the same wifi or one of those covered in the firmware package before you make changes, however!

Good luck! and be sure to search this forum for hints and help if you have a different card.

Also, if this is not the solution, I am sure some more knowledgable member will have answers.

This forum has a lot of good info.

Cheers,

Dave

---

### Post by egdisco on 2011-07-04
Thanks for the help, I am going to try it now.

---

### Post by egdisco on 2011-07-16
This doesn't work. I've tried various other things, but to no avail.

Anyone else with some ideas?

---

### Post by nm_geo on 2011-07-16
> **egdisco said:**
> Hi,
I have seen other threads, and have tried to do it manually by reading the threads through but I can't solve this.

I have a Dell Inspiron 1545, with Windows 7 installed. I have dual-booted it with Ubuntu but the wireless won't work due to it not having the right firmware.

I need help, as Ubuntu looks really good but I will (of course) need the internet on it. I can't connect it to my router via Ethernet cable as I have broken the port on my laptop (stupid thing to do, wish I hadn't).

Thanks for the help,
George.

Copy & paste in terminal

```
lspci -nn | grep 0280
``````
sudo lshw -C network
``````
rfkill list all
```Paste results here.. We will have enough to start

---

### Post by vavantoo on 2011-08-13
Hi,

I have the same problem. I am pasting my results, that you have asked for. 


[FONT=Trebuchet MS]ritwick@ubuntu:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
ritwick@ubuntu:~$ sudo lshw -C network
[sudo] password for ritwick: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:41:f6:01
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:5e:1b:da:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
ritwick@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ritwick@ubuntu:~$ [/FONT]


Hope to hear from you soon.
Ritwick

---

### Post by nm_geo on 2011-08-14
[vavantoo]("http://ubuntuforums.org/member.php?u=1401600")

Connect your ethernet in terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

This just make sure you are fully updated.
Then 

```
sudo apt-get install b43-fwcutter
``````
sudo apt-get install firmware-b43-lpphy-installer
```You can also install it from Synaptic.. Reload. Search on **[COLOR=Red]_bcm_[/COLOR]**

You probably already have b43-fwcutter installed but it will not hurt.

Let me know how it goes...

---

### Post by vavantoo on 2011-08-15
Hi,

@nm_geo
Thanks mate, the wireless connection has started to work. :D
Everything is working fine now on the Dell.
Thanks once again. :)

Cheers
Ritwick

---

### Post by nm_geo on 2011-08-15
You are very welcome Enjoy.

---

