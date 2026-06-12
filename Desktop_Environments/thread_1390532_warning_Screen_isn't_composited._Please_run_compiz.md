---
title: "warning: Screen isn't composited. Please run compiz (fusion) or another compositing m"
date: 2010-01-25
forum: Desktop Environments
---

### Post by dominican_dutchboy on 2010-01-25
warning: Screen isn't composited. Please run compiz (fusion) or another compositing manager

When i shut down i get this warning.  I have compiz installed, but for some reason it isn't working right.  also, the cube, and other features aren't working right.  Please help!

---

### Post by oldos2er on 2010-01-25
What video card do you have, and have you installed restricted drivers for it (if applicable)?

---

### Post by rahilm on 2010-01-26
did u mess up with xorg.conf ? and r u using avant-window-navigator?

---

### Post by dominican_dutchboy on 2010-01-27
I'm not entirely sure which video card I have. When I go to my hardware, nothing shows up.  Where else would I find this?
Also, i'm pretty sure I didn't mess up the xorg.conf, and I am using AWN.

Update: Now every time i start up, it says "Ubuntu is running in low graphics mode (EE): No device detected. 

It seems to be getting worse, even though I haven't done anything.

---

### Post by FreezWay on 2010-01-27
what does lspci give you?

---

### Post by dominican_dutchboy on 2010-01-27
lcpsi?

---

### Post by dominican_dutchboy on 2010-01-27
I ran lspci, here's what I got:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by muthiahmerchant on 2010-02-12
I am having the same issue now, this happened after doing an ubuntu update that I did and restarted. Also when i click on places - home folder i get a message "Could not open location 'file:///home/mxyz' No application is registered as handling this file"

---

### Post by Luisnux on 2010-02-12
I know that I had that issue at some point.  And if I'm not wrong you'll have to download the drivers.  To do that first make sure that you're connected to the internet, and then go to System-->Administration-->Hardware Drivers, then once it has detected your drivers you will have to restart to be able to use them.  Once you've enabled that then you can right click on your desktop, and go to Change Desktop Background--> Visual Effects and select Extra (This is provided that your video card has at least 64mb of memory).  After that it should be fixed.  Or at least I think that's how I fixed it.  If it does not work it will at least not hurt your system in any way.  If you don't have enough memory it will not let you select extra but other than that it should not cause any issues.

---

### Post by Hazelip on 2010-03-13
I just installed updates on 9.04 last night, put the laptop in suspend for the night, and when I lifted the lid this morning, I got this same error.

This sucks.

---

### Post by Random_Dude on 2010-05-29
I had some issues too after installing AWN.
I've got that same warning message when I logout and some startup applications appear in duplicate.:|

Does anyone know who to solve this?

---

### Post by hok00age on 2010-05-29
1. Go to System > Preferences > Appearance
2. Select "Visual Effects" tab
3. Click Extra
4. Then set your compiz preferences via ccsm

Hope it helps
Regards :)

---

### Post by Random_Dude on 2010-05-30
> **hok00age said:**
> 1. Go to System > Preferences > Appearance
2. Select "Visual Effects" tab
3. Click Extra
4. Then set your compiz preferences via ccsm

Hope it helps
Regards :)

Didn't work. :|
It's not a big deal. I get a warning message on logout, but somehow compiz still works.
The only thing bugging me are the duplicate startup applications.:mad:

Thanks anyway.;)

Cheers. :cool:

---

### Post by shai3421 on 2010-05-30
> **Random_Dude said:**
> Didn't work. :|
It's not a big deal. I get a warning message on logout, but somehow compiz still works.
The only thing bugging me are the duplicate startup applications.:mad:

Thanks anyway.;)

Cheers. :cool:

Go to System -> Preferences -> Startup Applications

You can remove the duplicates from there.

---

### Post by Random_Dude on 2010-05-30
> **shai3421 said:**
> Go to System -> Preferences -> Startup Applications

You can remove the duplicates from there.

That was the first thing I tried.
The problem is that it only shows one (not two). When I disable it, that application stops to appear duplicate (it appears only once), but doesn't go away in startup, which means, that I can't disable it completely from startup if I want to.

There is probably some register of the startup applications in some file on the system. Does anyone know how to access such a thing through the CLI? :confused:

Thanks. ;)

PS: the applications are Skype and a terminal desktop

---

