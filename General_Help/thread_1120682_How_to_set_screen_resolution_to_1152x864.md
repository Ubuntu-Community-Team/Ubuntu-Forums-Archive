---
title: "How to set screen resolution to 1152x864"
date: 2009-04-09
forum: General Help
---

### Post by StarryKnight on 2009-04-09
I know its been asked many times, and i did search around here, but its just not working whatever i tried writing to the xorg.conf file, maybe the solution doesn't apply to my monitor?
My monitor is being correctly detected as a Compaq, refresh rates and everything is fine, just the resolution is just at 1024x768 85hz, the only higher resolution is 1280x1024 but offers only 60hz to me. 

I'm a new user to ubuntu, in fact installed just today (but was using it in live mode for some time). The default recommended resolution which i'm used to working was 1152x864, now everything just looks so big, it would be a BIG help if you helped, please :)

Here's my xorg.conf file

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
EndSection


Thanks!

---

### Post by khelben1979 on 2009-04-09
First it's interesting to see what graphics card/chip you have over there:

```
sudo lspci
```

Then download and install the appropiate drivers (have you tried this?).

---

### Post by StarryKnight on 2009-04-09
Its just the integrated intel extreme graphics on my old computer :). 
Hence so its just so much more remarkable how much graphics ubuntu can extract out of this!

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by khelben1979 on 2009-04-09
I really didn't like that xorg.conf file. Normally it should contain much more information, where you have the possibility to add this new screen resolution just by editing the xorg.conf file, **after**, you have made a backup on the file. :)

At the present I'm not sure what you should do. If you had ATi or nVidia, it would be easier to fix this, I think.

---

### Post by KeyserSoze93 on 2009-04-09
The new xorg config system is really ill conceived. Yes, Xorg is usually good at detecting the hardware at runtime, but if it makes a mistake, there is no obvious way to override in unless you have an old xorg.conf lying about (like I do).

On one occasion, when I needed to force a Debian machine to do Xinerama, I did it by hacking my own xorg.conf (even though the hardware was entirely different, it was still easier then making the machine write one itself)

A very round about method might be that if you have an old Ubuntu Live CD lying around, which an old xorg on it, then running that may write a config file to the Live CD's ram disk, with all the modelines etc. for your monitor, which you can then copy into you real installation.

---

### Post by StarryKnight on 2009-04-09
Thanks for your replies guys... damn, then am i stuck with 1024 for good? :( 
should i try whats being suggested [here]("http://ubuntuforums.org/showthread.php?t=188556"), after backing up of course, though i doubt it will work cause its probably for an older ubuntu and nvidia...

and nope i don't have an older ubuntu cd, i might be able to find it on bittorrent though...will it be useful? if yes then what version should i get?

---

### Post by StarryKnight on 2009-04-09
And would this command help? ```
gksu displayconfig-gtk
```

---

### Post by StarryKnight on 2009-04-10
Well so i used the above code, a window popped up with all the monitor details and the facility to select a different monitor and even to add a monitor model. 
I went ahead and added the .inf file from the monitor's drivers which i used for windows. After this, the 1152... resolution was visible in this dropdown on the window, and the changes were to be applied after a logoff.

I did so, but when i returned, the change screen resolution from the system menu, just displays the old values of resolutions :( without the 1152 :( I again looked up the xorg.conf file, and it looks a lot more interesting now,
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"COMPAQ"
	Modelname	"COMPAQ 7500 Color Monitor"
	Horizsync	30.0-70.0
	Vertrefresh	50.0-140.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@85"	"1024x768@75"	"832x624@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"1024x768@43"	"800x600@75"	"1152x864@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@85"	"1400x1050@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Can you help me now guys??

---

