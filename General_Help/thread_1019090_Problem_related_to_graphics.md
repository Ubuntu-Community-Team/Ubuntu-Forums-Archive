---
title: "Problem related to graphics"
date: 2008-12-22
forum: General Help
---

### Post by rotogenray on 2008-12-22
When I first installed Ubuntu, I had the same problem I'd had with all other linux distros- screen resolution. I fixed that in fedora, but still found fedora to be just overly difficult to use.

After going from debian to fedora to ubuntu 64 bit I finally settled on ubuntu. I edited the xorg.confg wrong (its barely there anymore.. oops) but ubuntu came up in low graphics mode- which, on my screen is 1280 by 1024.

So I didn't worry about it... until now.

 I think it might be neat to have some desktop effects... or to be able to play videos that aren't framey or just plain glitchy (they sometimes like to stop- but if I continue to move my mouse while they're playing they play alright.)

As well I just think its having side effects where the stability over time of a program sitting idle decreases... then videos don't want to play at all or I lose sound and I just restart and everything's hunky dory again.

My monitor is a HP vs17e lcd monitor
horizontal refresh rate 30-83 khz
verticle refresh rate of 50-76hz

I think the default depth was 24...
I think my graphics card is nvidia something... that i'd have to check but i'm not sure you need it.

I know generally how to edit this, but I can't find a complete version on the internet of xorg.confg for ubuntu

I love ubuntu, still wouldn't use windows again if you paid me... though xp wasn't all that bad with open office and firefox...



I'm looking for a complete xorg.confg

---

### Post by sedawk on 2008-12-22
To get a fresh xorg.conf run command line tool "dexconf"

You can list your graphic adapter with all other pci devices, using
command line tool "lspci"

Best way to get nvidia's drivers properly working is to run (via menu) System->Administration->Hardware Drivers.

---

### Post by rotogenray on 2008-12-22
> **sedawk said:**
> To get a fresh xorg.conf run command line tool "dexconf"

You can list your graphic adapter with all other pci devices, using
command line tool "lspci"



When I try to run dexconf I get the following:

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
dexconf: error: unable to write to "/etc/X11/xorg.conf"

I tried running it as root user, but no luck still

Here is the output from lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

### Post by rotogenray on 2008-12-22
This might help- the error that makes ubuntu revert to low graphics mode says that it can't find a valid framebuffer device and the screen isn't compatible with whatever settings.

The framebuffer error is of concern to me. How do I fix this?

---

### Post by WillBMX on 2008-12-23
What you need to do is right click on 'Applications', then click 'Edit Menus'. In the box that appears, on the left-hand column (Menus) click on 'Other', then one of the options that comes up on the right-hand list will be 'Screen and Graphics'. Chedck the box then close it.
Click Applications>Other>Screen and Graphics and a box will appear which lets you manyually tell the computer which screen and graphics card you are using. The computer will then offer you the options to change the resolution and refresh rate to whatever you want, if its compatible with the screen and graphics card you are using. So find your screen and graphics card from the lists, tweak with the settings so they're right, then click 'OK' and the window will disappear. Then try rebooting and it should boot up in normal mode rather than low graphics mode.
:) good luck.

---

### Post by rotogenray on 2008-12-23
> **WillBMX said:**
> What you need to do is right click on 'Applications', then click 'Edit Menus'. In the box that appears, on the left-hand column (Menus) click on 'Other', then one of the options that comes up on the right-hand list will be 'Screen and Graphics'. Chedck the box then close it.
Click Applications>Other>Screen and Graphics and a box will appear which lets you manyually tell the computer which screen and graphics card you are using. The computer will then offer you the options to change the resolution and refresh rate to whatever you want, if its compatible with the screen and graphics card you are using. So find your screen and graphics card from the lists, tweak with the settings so they're right, then click 'OK' and the window will disappear. Then try rebooting and it should boot up in normal mode rather than low graphics mode.
:) good luck.

I get into the menu, and select "other"

screen and graphics isn't available to be added.

I'd previously added most available menu items... is there any way for me to access this?

---

