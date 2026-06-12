---
title: "Upgrade from 9.04 to 9.10"
date: 2010-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by navderm on 2010-02-17
Hi All,

I recently made a blunder, of upgrading from ubuntu 9.04 to 9.10. I should have listened to peoples advices...
anyways....


there are a couple of problems i am facing. 

1. My touchpad is not working
2. My sound card is not detected
3. My video card is not detected.

I have tried various methods told in various websites but nothing is helping.

I am pretty new to linux platforms and hence can't really do too much myself.

Kindly please help. 

Sincerely,

---

### Post by navderm on 2010-02-17
Hi
I am updating my output of lspci






00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

---

### Post by bobcollard on 2010-02-19
There is only one solution, install the full version 9.10 from scratch.  Don't forget to backup your home folder, just the visible files like Documents, Music, Pictures, etc.

---

### Post by 1337-h4xx0r on 2010-02-20
9.10 is very buggy, glitchy, and doesn't work on my Dell Studio 1555. I would not recommend upgrading to the 9.10. Perhaps, downgrade since you already did?

---

### Post by coffeeaddict22 on 2010-02-21
Like rules, programs are made to be ... explored.  Given sufficient exploration, most programs become buggy.  I'm running 9.10 on a Studio 17 with no problems.
A clean install is often a good idea.  If you do that, I'd strongly encourage you to partition up your hard drive, and create a /data partition to keep the stuff you don't want to have to reinstall with each upgrade.  /home is OK, but there's a whole lot of configuration files that end up in it (network card drivers for ndiswrapper and Gnome config files I've had trouble with in the past), and so it's a good idea to be able to choose how much of /home you keep from one install to the next.

However, from what you've said is wrong, there's possibly a few easy fixes.

For the video card, have you enabled the restricted driver?  The option should have been given on install, if not it's in System/Adminstration/Hardware Drivers.

Sound: the most common problem is the mixer volume is set to 0.  Open a terminal (Applications/Accessories/Terminal) and type in ```
alsamixer
```; have a look to see what the settings are at.  it's a terminal, but you can use the arrow keys to get around.  There's a really good sound troubleshooter kept [here;]("http://ubuntuforums.org/showthread.php?t=205449&page=87") have a look for more ideas.

For the touchpad, is it not working at all?  In the terminal, type in ```
xev
``` move your mouse up to the square and see if there's any output.  If there is, your touchpad is sending events and you've got the recognition turned off.  There's sometimes a switch just above the pad that you may have knocked.

Post back if you need more help.

---

