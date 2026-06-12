---
title: "Screen Res. automagically drops to 800x600 --stuck"
date: 2008-01-09
forum: Desktop Environments
---

### Post by espo111 on 2008-01-09
Upon a reboot, my screen resolution dropped to 800x600 60hz regardless of what my xorg.conf says.

I am using an old voodoo3 video card (my geforce4 blew a capacitor)  which used to work great. I cant change anything in the GUIs; they only give me the option of 800x600 or less.

when i try to change the screen and graphics preferences, it crashes.

when i pick my actual monitor i get an almost unreadable screen.

i have tried  _sudo dpkg-reconfigure xserver-xorg_ and nothing.


in my xorg.cof it says "failsafe" but i don't know what that means, but it does not sound good.


any ideas would be appreciated

~


_**xorg.con**_
```

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:9:0"
	Driver		"tdfx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 997DF/927DF/997MB/927MB/927DFI/927MBI"
	Horizsync	30-96
	Vertrefresh	50-160
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
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@85"	"800x600@56"	"1024x768@75"	"640x480@85"	"1024x768@70"	"640x480@75"	"1024x768@60"	"640x480@72"	"1024x768@43"	"640x480@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1792x1344@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Coreigh on 2008-01-10
I had this problem yesterday, xorg continually uses the 'failsafe' instead of the 'real' config file.

switch to an alternate tty by pressing Ctrl F2
log in
rename the failsafe file --> sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.BAK
sudo will ask for your password
change back to the graphical display by Ctrl F7
press Ctrl Backspace to kill xorg

When xorg restarts it *should* use the regular xorg.conf 

--good luck

---

