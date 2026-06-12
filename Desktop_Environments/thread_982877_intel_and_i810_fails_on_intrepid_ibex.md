---
title: "intel and i810 fails on intrepid ibex"
date: 2008-11-15
forum: Desktop Environments
---

### Post by alternotgoto on 2008-11-15
Hi there, 3rd post on my first day, wow!

Problem for you guys, and see if anybody knows the solution.

Have an old HP machine (using intrepid ibex - fully up to date) with the following chipset...

[COLOR="Blue"][FONT="Courier New"]install@cleverdix:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)[/FONT][/COLOR]

Trying to get this working with the intel or the i810 drivers for xorg Although what the difference between these two confuses me, because they are soft-linked in the /usr/lib/xorg/modules/drivers

[FONT="Courier New"][COLOR="Blue"]install@cleverdix:/usr/lib/xorg/modules/drivers$ ls -l *i810*
lrwxrwxrwx 1 root root 12 2008-11-13 22:30 i810_drv.so -> intel_drv.so.
[/COLOR][/FONT]

Anyways, if I use the xorg at the bottom of this post with "intel" in the driver for the device section, then when I start X, it crashes with the following:


[COLOR="Blue"][FONT="Courier New"](II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb80a2400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b190dd]
3: /usr/bin/X11/X [0x80caec4]
4: /usr/bin/X11/X [0x80cb02a]
5: /usr/bin/X11/X(xf86HandleColormaps+0x21a) [0x80cbf3a]
6: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b1bd70]
7: /usr/bin/X11/X(AddScreen+0x19f) [0x807137f]
8: /usr/bin/X11/X(InitOutput+0x206) [0x80aa536]
9: /usr/bin/X11/X(main+0x279) [0x8071b19]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cab685]
11: /usr/bin/X11/X [0x8071101]
[/FONT][/COLOR]

Now if I try this with i810 in the device section under driver then I get the following.

[COLOR="Blue"][FONT="Courier New"](II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: 
(EE) No devices detected.

Fatal server error:
no screens found
[/FONT][/COLOR]

Two things:

[LIST]
[*]Frstly anybody else had this problem and is it a bug? If so will revert to Hardy?
[*]Secondly, and for my own curiosity; why should changing the device driver entry from i810 to intel make a difference when they are soft-linked to each other. Is there some jiggery-pokery going on in the driver to know how it is called?
[/LIST]

Many thanks in advance.

Cheers

attaching xorg.conf for your perusal.

[COLOR="Blue"][FONT="Courier New"]install@cleverdix:/usr/lib/xorg/modules/drivers$ cat /etc/X11/xorg.conf
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Vendorname	"Intel"
        #Option          "XVideo" "true"
        #VideoRam         131072
        #Option          "DRI" "true"
	#Option		"AddARGBVisuals"	"True"
	#Option		"AddARGBGLXVisuals"	"True"
EndSection


Section "Monitor"
	Identifier	"Monitor[0]"
	Vendorname	"Iiyama"
	Modelname	"Iiyama Prolite E485S"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 0 "Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection


[/FONT][/COLOR]

---

### Post by ronnielsen1 on 2008-11-15
I have the exact same chipset and intrepid gave me 3d with no problems using xserver-xorg-video-i740 and xserver-xorg-video-intel installed. Does the 740 driver not work for you?

---

### Post by alternotgoto on 2008-11-15
Thanks for the response. Tried that and no joy, unfortunately. When I try the i740 module, it is telling me there are no matching devices on the BusIDs. Check about 11 of them and gives up with "No devices detected".

---

### Post by ronnielsen1 on 2008-11-16
> ron@ron-desktop:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


That's strange. My card is listed above and gets picked up on automatically. Put a live cd of 8.10 and see if it picks up correctly.

---

### Post by timjohn7 on 2008-11-16
I have also had this problem on a Fujitsu Siemens Amilo notebook (on Hardy and Intrepid).  After numerous unsuccessful attempts at fixing the problem, it seemed to resolve itself after updates and various xorg.conf variations.  What also seemed to help was plugging in of an external projector/monitor.  This gave some weird output (massive screen resolution) but thereafter, the machine booted correctly with stock standard 1024 x 768 resolution and has been fine ever since.
There are threads going around saying that xorg.conf is no longer accessed, and there are a couple of bug reports about the problem, but with my hand firmly touching wood, everything is fine.
Apologies that this is less than helpful in terms of solving your problem; see it rather as inspiration that the problem can be solved.
Here is my xorg.conf which does seem to bear out the "unused" report.

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by shof2k on 2008-11-16
The i810 driver no longer exists in Intrepid.  It is now replaced by the intel driver; this is the reason why the i810 is soft-linked to intel.  This is also shown if you look for the driver in synaptic.  I think the aim is to have all intel based video covered by one driver.

I have an intel 845G based laptop and compiz no longer works.  In fact, xorg takes up all my CPU, so I'm using Hardy until I can figure out how to fix this.

Looking at [http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810") it suggests there is a known issue with the new version of xorg and the intel driver for intel based cards.  I'm afraid, unless you can help with the bug reporting, you might need to stick with Hardy (8.04).

If you do want to stay with Intrepid, you can add the following lines to xorg.conf.  They may help by tuning xorg.
```

	Option 		"AccelMethod" 		"exa"
	Option 		"MigrationHeuristic" 	"greedy"

```

---

### Post by stuartk on 2008-11-19
> **shof2k said:**
> The i810 driver no longer exists in Intrepid.  It is now replaced by the intel driver; this is the reason why the i810 is soft-linked to intel.  This is also shown if you look for the driver in synaptic.  I think the aim is to have all intel based video covered by one driver.


If you do want to stay with Intrepid, you can add the following lines to xorg.conf.  They may help by tuning xorg.
```

	Option 		"AccelMethod" 		"exa"
	Option 		"MigrationHeuristic" 	"greedy"

```

8.10 here on an HP Compaq d530 SFF. The chipset is i810.

8.04 ran very well. 8.10 had slow graphics, especially screen refreshes. Switching virtual desktops was painful, and even scrolling through a web site in Firefox sometimes was like wading through mud.

I just tried the Options you provided, and they helped quite a bit. I still don't think that it's as snappy as 8.04 or previous, but it's improved enough that I'm no longer thinking of going back to 8.04. 

Thanks for the info! :)

---

### Post by jnewm on 2009-03-02
Thanks so much shof2k, those options make a huge difference for me too.  Also, not to hijack this post, but I saw in another post a recommendation to switch from the Mesa to the Intel i810 driver...  I saw that the i810 driver isn't included in Intrepid, but is it possible to add it and switch over?  And would that be worthwhile?

Thanks again!

---

