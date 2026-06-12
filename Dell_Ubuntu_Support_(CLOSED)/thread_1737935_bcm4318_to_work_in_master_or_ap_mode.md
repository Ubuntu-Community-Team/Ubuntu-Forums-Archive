---
title: "bcm4318 to work in master or ap mode"
date: 2011-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Greth Rain on 2011-04-24
hi everyone,
i have had some problems with ubuntu and had to reinstall and reconfigure...but now i am back.
My question:
I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
and i would like to turn it into ap mode. so far, i have downloaded the closed source driver and firware for linux and got it up and running, i do not use the ndiswrapper driver.
I was wondering if it is possible to turn it into AP so that i can use it to create a secure proxy connection (people tend to like to hack other peoples wireless and use it for free).
so anyway, i would like to turn a 5 year old Dell Inspiron 1300 into an AP for my house. also, rather that puttin g a mac filter etc... on my existing router, i would like to use the computer itself as i can then 'play' with the hackers (in other words mess around with them) using the upside-down-ternet guide.
is it possible to turn my computer into an AP?

EDIT:
i would like to have 4 or 5 devices connected to the host. 2 computers by wireless, 1 computer by ethernet and 1 phone by wireless.

Comp specs (not that good):
Intel Pentium M (1.73GHz, not OCed)
BCM4318 802.11g wireless card
80GB HDD

output from 'lspci'
> 
greth@greth-ME0512:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
greth@greth-ME0512:~$
Please tell me if I can turn my Dell into an AP!

---

