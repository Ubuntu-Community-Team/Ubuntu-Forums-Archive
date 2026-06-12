---
title: "Hibernate/suspend"
date: 2009-04-03
forum: General Help
---

### Post by johannes_h on 2009-04-03
I see many have this problem, that you cannot suspend/hibernate. Tho I can't find any real answers :S

Thanks..

---

### Post by logic++ on 2009-04-03
What is your hardware characteristics??? Can't help without this info.

---

### Post by johannes_h on 2009-04-03
Dell Vostro 1500. Why should that be important?:) I don't know which hardware you specific want to know. It's a laptop with Core2Duo T7300CPU, 2GB RAM..

---

### Post by logic++ on 2009-04-03
You should post the output of the command:
```
lspci
```
Actually, there is a 95% possibility that the specific hardware of each laptop causes these problems. 
For example, for my laptop it was the Graphic Card (NVidia 9600M) that caused the errors so I had to install manually the new driver from NVidia's site.

---

### Post by change_mode on 2009-04-03
Most of these problems are supposed to be fixed in the next kernel releases.

---

### Post by cottfcfan on 2009-04-03
ive just installed 9.04 beta but the suspend problem still exists with no network on resume with wireless.
I was hoping the problem would be solved by now, maybe it will be by final release.

---

### Post by paradigm2 on 2009-04-03
> **cottfcfan said:**
> ive just installed 9.04 beta but the suspend problem still exists with no network on resume with wireless.
I was hoping the problem would be solved by now, maybe it will be by final release.

It works for me on my Acer Aspire 5100 series, surprisingly.  You might consider going to the Jaunty forum or filing a bug report here if one has already not been filed:

[http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.wordpress.com/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

Maybe they can get a fix in before the actual release?

---

### Post by johannes_h on 2009-04-03
> **logic++ said:**
> You should post the output of the command:
```
lspci
```
Actually, there is a 95% possibility that the specific hardware of each laptop causes these problems. 
For example, for my laptop it was the Graphic Card (NVidia 9600M) that caused the errors so I had to install manually the new driver from NVidia's site.

Ahh.. ok here goes ;)

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Lol, can't say I understand much of it :)

Thanks for the help

---

### Post by logic++ on 2009-04-03
Check the following links (even though they refer to a previous model):

[http://ubuntuforums.org/showthread.php?t=850755]("http://ubuntuforums.org/showthread.php?t=850755")
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/")

and let me know if it help or else we'll go deep on it...

Regards

---

### Post by PRCalDude on 2009-04-03
> **logic++ said:**
> You should post the output of the command:
```
lspci
```
Actually, there is a 95% possibility that the specific hardware of each laptop causes these problems. 
For example, for my laptop it was the Graphic Card (NVidia 9600M) that caused the errors so I had to install manually the new driver from NVidia's site.

Hmmm...

Here's the output of mine:

> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


I think I'm having a video card problem also when I try to bring it out of 'suspend.'  I installed uswsusp per this thread:
[http://ubuntuforums.org/showthread.php?t=417964&page=2](http://ubuntuforums.org/showthread.php?t=417964&page=2),
but I still have problems getting it out of 'suspend' when the computer puts itself to sleep.  

How'd you install your video driver?

---

### Post by PRCalDude on 2009-04-03
> **logic++ said:**
> Check the following links (even though they refer to a previous model):

[http://ubuntuforums.org/showthread.php?t=850755]("http://ubuntuforums.org/showthread.php?t=850755")
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/")

and let me know if it help or else we'll go deep on it...

Regards

I think my swap partition is screwed up.  Here's the output of my /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9f221362-0551-4ec1-969e-f71dc7b983c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9ae64d31-2306-4948-9f75-4c59c13ba4a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Maybe I need to get rid of my uswsusp work-around and just fix my fstab file?

---

### Post by logic++ on 2009-04-03
@PRCalDude

As a first approach try disabling DRI from your xorg.conf file. If that doesn't work visit this thread:

[http://ubuntuforums.org/showthread.php?t=727371]("http://ubuntuforums.org/showthread.php?t=727371")

---

### Post by PRCalDude on 2009-04-03
> **logic++ said:**
> @PRCalDude

As a first approach try disabling DRI from your xorg.conf file. If that doesn't work visit this thread:

[http://ubuntuforums.org/showthread.php?t=727371]("http://ubuntuforums.org/showthread.php?t=727371")

I don't have "DRI" listed in my xorg.conf file:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


---

