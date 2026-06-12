---
title: "Problems after a fresh install 11.04"
date: 2011-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Timsworth on 2011-09-16
Hi guys.

I upgraded from 10.10 to 11.04 when it was released only to come across problems on my first reboot.  Now I've gotten around to fixing it, I tried several things but all to no avail, so I decided to do a fresh install.

Everything was fine to begin with, but then on my first restart, I get the same problem as last time.  So I shlump around for a bit to try to fix it but decide it was due to me accidentally disabling something Unity depends on through compiz, so I do another fresh install.

This time, just to make sure my suspicions are correct, I simply install it and then when I get onto the desktop I restart to see if the problem persists.  And it does.

[B]The problem is that after the first restart of a fresh install the screen turns black and I get a prompt telling me the following: 
'Ubuntu is running in low graphics mode.

 Your screen, graphics card, and input device settings
 could not be detected correctly.  You will need to
 configure these yourself'
[/B]

Then I'm lead to a prompt that gives me several options, but all paths are fruitless and seem to do nothing.

Ubuntu appears to run fine before I restart it for the first time, and despite what I install or don't install the same thing happens.

I've installed the Catalyst ATI driver and it happens, and I've also NOT installed it and it continues to happen.
I've looked online to several boards and have come across several 'solutions' including purging flgrx and installing ati and radeon drivers; reinstalling X; even simply installing ubuntu-desktop.  None of which have worked for me.

Here's the output of lspci from the command line after the problem's occurred:
'00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
'

Any help would be greatly appreciated.

Cheers.

---

### Post by technosysind on 2011-09-16
Have you tried booting through Ubuntu on USB flash drive? Try and tell if it works or not??

---

### Post by Timsworth on 2011-09-16
I'm typing this from an Ubuntu LiveCD, so it clearly works if I run it from my USB.

---

### Post by Timsworth on 2011-09-18
Still no success.  Anyone?

---

### Post by bredsj on 2011-09-18
I have exactly the same problem, except that I have upgraded from 10.10 to 11.04 and everything worked fine until the recent (last) update, when my problems started.

The results from lcpci are:


00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]
01:00.1 Display controller: ATI Technologies Inc Device 717f
02:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:05.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
05:05.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
05:05.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

---

### Post by mörgæs on 2011-09-18
If the problem is about screen card drivers, it is worth trying this thread:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

