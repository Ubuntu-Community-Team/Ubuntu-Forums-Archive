---
title: "Cannot use nvidia driver on external monitor?"
date: 2008-02-07
forum: Desktop Environments
---

### Post by ragrim on 2008-02-07
Im using ubuntu 7.10 and an Acer Travelmate 4234 which has a GeForce Go 7300 in it, now ive had Ubuntu 7.04 and 7.10 installed on this laptop before and everything was fine, but for some reaosn now when i use my BenQ T91W (19" Widescreen) i cant use my nvidia driver, it defaults to some piece of crap driver and runs 800x600 res.

ive tried reconfiguring X and editing my xorg.conf but to no avail, am i missing something here?

---

### Post by pytheas22 on 2008-02-07
make sure you have the proprietary nvidia driver installed, and make sure that xorg.conf is set up to use it for all devices on all screens, not the "vesa" driver (which sounds like it's what your system is defaulting to on the external screen).

If you type nvidia-settings in a terminal you will get a nice GUI to configure your screens; it might help you solve your problem.

---

### Post by ragrim on 2008-02-07
my xorg.conf is configured to use "nvidia" driver for both devices, and both devices have the correct resolutions set for them in the .conf, the nvdiai driver that was installed by the restricted [ackage manager had this problem and then i used Envy to install the latest which was successfull but it still cant use nvidia driver on my external monitor.

i cant access the nvidia settings when using the 2nd monitor, only when using the 1st, when on the 2nd monitor it tells me im not using an Nvidia driver and says to activate it via terminal and restart X, i do that and the driver still doesnt start.

now ive been doing some fiddling and ic ant even get any screen to display, after i boot i just get a vlack screen :(

---

### Post by pytheas22 on 2008-02-07
> i cant access the nvidia settings when using the 2nd monitor, only when using the 1st, when on the 2nd monitor it tells me im not using an Nvidia driver and says to activate it via terminal and restart X, i do that and the driver still doesnt start.

That's strange.  It sounds like the external screen might be trying to use a different X server, which would explain why it's disregarding what you have in xorg.conf.  Can you connect to the external monitor but disable the VGA-out to it (using your BIOS settings or function keys, for instance; on my laptop I can control the external VGA using a combination of buttons), and then try running nvidia-settings?  It might be able to detect the external screen and write an appropriate configuration.  Or maybe not, but it's worth a try.
> 
now ive been doing some fiddling and ic ant even get any screen to display, after i boot i just get a vlack screen

There should be automatically-generated backups of your xorg.conf file in your /etc/X11 directory that you can default to (note that they may be hidden).  Personally, I like to also save a working configuration to my desktop before I start screwing around.

---

### Post by ragrim on 2008-02-07
ok i got my screen back....

yeah my laptop has a fn+f5 to switch between screens, but it doesnt work in ubuntu. the nvidia settings is useless to me, any changes i make there are reverted to default when i restart X, only place i can make changes is via screens and graphics in the admin menu, which i use to disable my laptop screen and enable the external screen.

heres part of my xorg.conf which is now a mess

```
Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"BenQ"
	Modelname	"BenQ T903"
	Horizsync	31-83.0
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
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x960@60"	"1280x1024@60"	"1280x1024@75"	"1280x960@75"	"1152x864@75"	"1400x1050@60"	"1024x768@60"	"1400x1050@75"	"1024x768@70"	"1600x1200@65"	"1024x768@75"	"1600x1200@60"	"832x624@75"	"1792x1344@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" #       
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #       
	Identifier	"screen1"
	Device	on "Display"
		Depth	24
		Modes		"1280x960@60"	"1280x1024@60"	"1280x1024@75"	"1280x960@75"	"1152x864@75"	"1400x1050@60"	"1024x768@60"	"1400x1050@75"	"1024x768@70"	"1600x1200@65"	"1024x768@75"	"1600x1200@60"	"832x624@75"	"1792x1344@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #       
	Identifier	"monitor1"
	Vendorname	"BenQ"
	Modelname	"BenQ T903"
	Horizsync	31-83.0
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
Section "ServerFlags"
EndSection	"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x960@60"	"1280x1024@60"	"1280x1024@75"	"1280x960@75"	"1152x864@75"	"1400x1050@60"	"1024x768@60"	"1400x1050@75"	"1024x768@70"	"1600x1200@65"	"1024x768@75"	"1600x1200@60"	"832x624@75"	"1792x1344@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #       
	Identifier	"monitor1"
	Vendorname	"BenQ"
	Modelname	"BenQ T903"
	Horizsync	31-83.0
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
Section "ServerFlags"
EndSection
```

Why there is a BenQ T903 i dunno, i was testing differant monitor options to see if any worked and the T903 seems to have stuck.

---

### Post by ragrim on 2008-02-07
made some progress, using X -configure i can now use 1440x900 res, but i still cant load nvidia drivers while using my 2nd monitor. stupid drivers!

---

### Post by pytheas22 on 2008-02-07
can you post your entire xorg.conf please?

---

### Post by ragrim on 2008-02-07
i would but ive given up and cracked the shits, just formatted my drive cause i was also having troubles getting into windows with a dual boot, stupid recovery partitions.

---

### Post by pytheas22 on 2008-02-07
ok, sorry it didn't work out.

---

