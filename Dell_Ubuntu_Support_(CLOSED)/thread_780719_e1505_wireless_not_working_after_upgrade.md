---
title: "e1505 wireless not working after upgrade"
date: 2008-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by treeclimber on 2008-05-03
I just upgraded my OS to Hardy Heron on my e1505 (purchase last June with Ubuntu) and everything went OK, except now my wireless will not connect.  It was working fine before.  It immediately looks for the connection, but just won't connect.  I had some trouble before the upgrade with getting kicked off my connection.  Can anybody help me?  I figure it is a fairly simple fix.  It seems to detect my network card, so that isn't the problem.  It also seems to detect the wireless connection.  It just won't connect.  Thanks for any help you can give me.

---

### Post by linuxnoob1 on 2008-07-10
Same here.  I used the tutorial for the E1505 to get my wifi working under Gutsy, but as soon as I updated, all functionality failed.  I tried wiping and reinstalling fresh with Hardy, but after trying different guides and such, I still have had no luck.
Any ideas?

---

### Post by PinkFloyd102489 on 2008-07-10
What's the chipset on the wireless card?

Do in the terminal:
```
lspci
```

And paste it here.

---

### Post by falcon61102 on 2008-07-11
To go along with 
```
lspci
```
type in and post the results of:
```
lshw -C network
```

---

### Post by linuxnoob1 on 2008-07-11
Here is the output from what you suggested:
[INDENT]output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
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
       serial: 00:15:c5:03:14:76
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.7.92 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

[/INDENT]

Thanks for the reply, I hope we're able to get it working

---

### Post by falcon61102 on 2008-07-11
If you look at the end of the second to last line of that code you're going to see a bit that says Module=ssb... that's your problem (or at least one of them.)  Follow this link and you should be able to get it going:

[http://ubuntuforums.org/showthread.php?t=851465&page=2](http://ubuntuforums.org/showthread.php?t=851465&page=2)

If you look on page 2 of the thread, you can see where I started posting.  And there are more links on one of my posts there in case that doesn't work.

What this is going to do is Blacklist SSB, remove the module and then load ndiswrapper and you should be good to go.

---

### Post by linuxnoob1 on 2008-07-11
It seems that ssb is being used by another module (b44 I think)
I added ssb to the blacklist, but each time I try to use rmmod, it says the module is in use, even after a restart.  I am confused.  I used ndiswrapper successfully and easily under feisty, and then gutsy, but I just keep hitting a brick wall here.  I do not want to use the standard drivers, I am dual booting with windows and do not want to mess with firmware.  Is there something I am missing with blacklisting ssb?
Here is the output from the commands stated in your other thread.
[INDENT]cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
etc.
etc.
blacklist b43

# Get rid of SSB
blacklist ssb

#sudo modprobe -r ssb
FATAL: Module ssb is in use.

#sudo rmmod ssb
ERROR: Module ssb is in use by b44

ndiswrapper is already loaded in my modules, and the other threads seem to be in favor of installing the b43-fwcutter firmware.

[/INDENT]
So that's what I got, I'm pretty stumped
Thanks for your help

---

### Post by falcon61102 on 2008-07-11
Try adding blacklist bcm43xx and running it.  Restart would help after blacklist add.

---

### Post by falcon61102 on 2008-07-11
Also you going to have to remove the previous modules to load ndiswrapper, do this by:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod ssb
```

Then try loading ndiswrapper.  Sorry, forgot that earlier.

---

### Post by linuxnoob1 on 2008-07-11
Okay, I did all of those.  As soon as I disable b44, my wired lan connection went out.  I went ahead and diabled ssb, then I used modprobe ndiswrapper to load it.  On a random guess, I reenabled b44 and now have a working wireless connection.  The question is, how do I get it to do that in the future without loading ssb in the first place, and loading ndiswrapper first.  Thanks for the help, this is a good victory.

---

### Post by falcon61102 on 2008-07-11
Glad you got it working.  To have those settings load everytime you start up you need to:
```
sudo gedit /etc/modules
```
Add ndiswrapper to the last line, save and close.  

Now ndiswrapper will start everytime you boot up.  Is that what you're looking to do, sorry got a little confused by your last post on what you are exactly looking at.

---

### Post by linuxnoob1 on 2008-07-14
I tried that, but the system still loads b44, and subsequently ssb on restart, even though ssb is blacklisted
Would it work to blacklist b44, then load it after ndiswrapper in modules?
Right now when I start, if I remove b44, then ssb, then load ndiswrapper and reload b44, my wireless card comes up.  I just don't understand why it is able to load ssb event though ssb is blacklisted.  Thanks for the help, it's nice to be able to use wireless again.

---

### Post by linuxnoob1 on 2008-07-14
From thread : How- To: Dell 1390 WLAN 1390 WLAN (Broadcom 4311 [14e4:4311]) for Laptops using ndiswrapper (Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Tutorials and Tips it is on the first page a few posts after the main one.
> **Champers said:**
> Well, after running 

```
modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

my internet finally worked after 3 days of googling tutorials lol

I found this in the original guide I used that failed to work.  I think it's the solution to my problem.  I'll post back

---

### Post by linuxnoob1 on 2008-07-14
OK, final product.  My computer boots and connects to a wireless network automatically.  To finally get it working, I removed ndiswrapper from my modules, and edited /etc/rc.local as follows:
> [INDENT]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[B][U]
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44[/U][/B]

exit 0[/INDENT]

it effectively removes and then reloads all the necessary modules, and finally, I have wireless again.  I am surprised at what a hard time I've had upgrading to a new release of Ubuntu, I guess that's the nature of software, it sometimes just doesn't work the way it's supposed to.

---

