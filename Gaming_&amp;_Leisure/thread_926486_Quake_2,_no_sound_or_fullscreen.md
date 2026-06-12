---
title: "Quake 2, no sound or fullscreen"
date: 2008-09-22
forum: Gaming &amp; Leisure
---

### Post by thedudething on 2008-09-22
I tried installing using the libc package but it didn't work for me so I tried the Loki installer for it.

It installed and it plays but I can't play it fullscreen, there is no sound and I can't see the crosshairs. Can someone help me with this?

---

### Post by Crafty Kisses on 2008-09-22
I'd like to see the results of this command:
```
lspci
```

---

### Post by thedudething on 2008-09-22
administrator@administrator-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by chungy on 2008-09-22
There really aren't any maintained ports of Quake II anymore that preserve the look & feel of the original game (there's tons of them that greatly modify visual elements and gameplay elements, some of which don't even support Quake II itself), at least none that I have been able to find.  I had to bite the bullet and just run it in Wine, which seems to work well enough.

It's pretty discouraging really; I can get ports of most other id games that preserve the feel and gameplay elements of other id games (Wolf3D with Wolf4SDL, Doom/Doom2/Final Doom with Chocolate Doom, Quake I with TyrQuake, and Quake III Arena with ioquake3), but not Quake II for some odd reason.

---

### Post by thedudething on 2008-09-22
Lol yeah, I don't actually like having enhanced versions, i'm a sucker for the classics and authenticity.

Unfortunately I can't run it on wine because I bought it off steam :(

---

### Post by chungy on 2008-09-22
Ah, well I have the pressed CD-ROM version (as well as the Steam version, I just wanted the mission packs for it :P)...

You should be able to download the un-Steamified Windows binaries and run it fine (the Steam version should run fine too, it just takes a huge amount of time to load, for logging into Steam): [ftp://ftp.idsoftware.com/idstuff/quake2/](ftp://ftp.idsoftware.com/idstuff/quake2/)
Just get q2-3.20-x86-full-ctf.exe and extract it with unzip over your steam copy (copy your Steam/steamapps/common/quake 2/ directory if you don't want your regular copy modified), and it should run just like the original non-Steam game. :)

I also have a distaste for enhanced ports when I just want to play the *original game*.  They're fine and great for custom WADs/mods with new content, but for original games, I want to play it just like the original versions!  Only one port (Chocolate Doom) really goes out of the way to make sure *nothing* is unlike the original; although for things like TyrQuake and ioquake3 which have bug fixes, raised limits, and minor feature additions that make no real gameplay changes (they still support original demos), I'm fine with them.

---

### Post by thedudething on 2008-09-22
Thanks man, that was a big help, too bad I couldn't get it onto my ubuntu file system :(

Steam should make a linux version for all the ID games...

---

### Post by Brebs on 2008-09-22
> **chungy said:**
> preserve the look & feel of the original game
What's the issue exactly? Better graphics? Those can be stripped from the .pk3/.pak files if you so desire.

You probably want [Quetoo](http://bugs.gentoo.org/show_bug.cgi?id=154292). Although I'd recommend [Kmquake2](http://ubuntuforums.org/showthread.php?t=890091).

---

### Post by thedudething on 2008-09-23
Na I want the same gfx as the original

---

### Post by swoody on 2008-09-23
thedudething - besdies this, have you had any other issues playing Quake 2? My brother has it, but I don't know if it would be worth the hassle to get it to work or not.

---

### Post by eragon100 on 2008-09-23
Do you have the windows quake 2 disc?

To preserve your sanity, use wine. (and, no, I don't mean, drink away the depression :lolflag: )

Just double click setup.exe on the cd-rom, follow the installation procedure (select maximum install size so you don't have to put the cd in the drive if you want to play) and then run it by going to

applications -> Wine -> Browse C:\ Drive

On the wine C:\ drive, open the folder quake 2 and double-click on quake2.exe.

Have fun! :wink:

---

### Post by thedudething on 2008-09-23
My other problem is when I just type "quake2" in the terminal to run, it says sdlquake not found

---

### Post by GSZX1337 on 2008-09-23
> **eragon100 said:**
> Do you have the windows quake 2 disc?

To preserve your sanity, use wine. (and, no, I don't mean, drink away the depression :lolflag: )

Call me what you will, but I don't want to use Wine to run a native Linux game on my box. (although, I might end up doing doing the other thing if I can't get it running soon).

---

