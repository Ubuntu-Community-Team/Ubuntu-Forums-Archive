---
title: "1440 x 900 on Nvidia 5200 AGP card?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by SpencerStarnes on 2006-09-20
Hey, I've looked all over the interwebs, searching the tubes. I can't seem to find how to get a 1440 X 900 (16:10) wide resolution on Ubuntu Dapper. 

I have found alot of things talking about laptops, and intergrated Graphics. 
Will those work for me?

Beh, this is confusing stuff. 
Im also very, VERY new to anything non-windows. (5th day!!)
so. this would be great if you guys would help me out! ^_^ 
thanks.

---

### Post by linuxbz on 2006-09-20
I got an nVidia 5200 AGP working at 1680x1050 on a ViewSonic VX2025wm flat panel (LCD).  I tried lots of things that did not work until I saw a comment somewhere that the 5200 will NOT drive the monitor fast enough using the DVI (digital) connection. I hooked it up using the analog cable and it worked fine.

Are you running a CRT or LCD display, and using a digital or analog cable?

---

### Post by qpieus on 2006-09-20
I'm running a 19" LCD (viewsonic va1912wb) with that resolution on an analog cable (haven't tried the DVI conn. yet) using a FX6100 onboard video. Granted a FX5200 is slightly less power, but not much, so it should work ok. Also, I made the following changes on an old geforce mx400, and it now displays at 1440x900 too.
Anyway, to get (k)ubunutu to give me the right resolution I had to edit the /etc/X11/xorg.conf file to add in that resolution and the appropriate modelines.
In xorg.conf I added the following to the area of the file labeled:
Section "Monitor"
These are the modelines I added:```
  modeline  "1440x900@70" 126.98 1440 1536 1688 1936 900 901 904 937 -hSync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hSync +vsync


```
I got the modelines from googling my monitor model# plus "modelines" and luckily found a forum somewhere that had the info I needed. I also added the following to the area of the file labeled: Section "Screen"```
SubSection "Display"
    depth 24
    virtual 1600 1200
    modes "1440x900@70" "1440x900@60"

```
The 60 and the 70 are Hz.
So, for me, these changes allowed 1440x900 resolution to become available as a selection when you go to change the resolution.
So I suggest you google for your monitor's correct modelines and make similar changes to what I did. There are websites that will calculate the modelines for you also.

Here's the video/monitor sections of my xorg.conf file:```
Section "Monitor"
  identifier "VA1912wSERIE"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  HorizSync	30.0 - 82.0
  VertRefresh	50.0 - 85.0

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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1440x900@70" 126.98 1440 1536 1688 1936 900 901 904 937 -hSync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hSync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync

  gamma 1.0
EndSection

Section "Device"
  identifier "Generic Video Card"
  boardname "NVIDIA GeForce FX (generic)"
  busid "PCI:0:5:0"
  driver "nvidia"
  screen 0
  vendorname "NVIDIA"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Generic Video Card"
  Monitor "VA1912wSERIE"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1600 1200
    modes "1440x900@70" "1440x900@60" "1280x1024@75" "1280x960@60" "1280x854" "1280x1024@60" "1152x768@54" "1280x960@75" "1152x864@75" "1400x1050@60" "1024x768@60" "1400x1050@75" "1024x768@70" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56"
  EndSubSection
EndSection

```
I have a bunch of resolutions in there I'll never use, need to delete those....
Good luck!

---

### Post by SpencerStarnes on 2006-09-20
okiedokie. 

I cant find the mode lines 

I found THIS site. 

[http://forum.mandrivaclub.com/viewtopic.php?p=218606&sid=36709e984aa669b7a520261ebf6913ed](http://forum.mandrivaclub.com/viewtopic.php?p=218606&sid=36709e984aa669b7a520261ebf6913ed)

eeh, so some one help me out. How do I do this, exactly. 
(treat me like a grandma, because I dont know at all.. ;_;)

---

### Post by SpencerStarnes on 2006-09-20
> 
Section "Monitor"
    Identifier     "H191W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "H191W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x1440" "1280x1024" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection



this is what my Xorg.conf looks like

---

### Post by linuxbz on 2006-09-21
Your first mode in each depth says "1440x1440"; it should be "1440x900". That may not be the only problem, but the 1440x1440 looks like a typo.

---

### Post by qpieus on 2006-09-21
> **SpencerStarnes said:**
> okiedokie. 

I cant find the mode lines 

I found THIS site. 

[http://forum.mandrivaclub.com/viewtopic.php?p=218606&sid=36709e984aa669b7a520261ebf6913ed](http://forum.mandrivaclub.com/viewtopic.php?p=218606&sid=36709e984aa669b7a520261ebf6913ed)

eeh, so some one help me out. How do I do this, exactly. 
(treat me like a grandma, because I dont know at all.. ;_;)

Do you have a 19" LCD Envision (that is referenced in this thread you found?) If yes, then you could use the modelines mentioned there. Be sure to backup the xorg.conf file before playing with it!
That thread has the following modeline:```
ModeLine "1440x900_60" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
```
Add that to you xorf.conf file in the Section "Monitor" along with the HorizSync 31-83 and VertRefresh 56-75 data.
So it should look something like:```

Section "Monitor" 
 Identifier "monitor1" 
 VendorName "Plug'n Play" 
 ModelName "H191W" 
 HorizSync 31-83 
 VertRefresh 56-75 

 ModeLine "1440x900_60" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync

EndSection 


```
Also make the change linuxbz said, 1440x1440 is not right in your file.

---

### Post by fragos on 2006-09-21
I run 1440x900 with an FX5200 DVI.  It works great with the VA1912wb LCD.  The video specific lines from my /etc/X11/xorg.conf follow:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Viewsonic VA1912wb"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Viewsonic VA1912wb"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
EndSection

You can also use the text based xorg configurator in a terminal window with command:

sudo dpkg-reconfigure xserver-xorg

This sets everything in xorg with a Q&A session.  If your unsure of any response select the default which may even be blank.  This will reset you selected video driver to "nv", the open source Nvidia 2D driver.  Just edit xorg.conf to change "nv" back to "nvidia" as in the lines that follow.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by benfreed on 2007-01-02
yes it works!!! so simple, i wish i tried before i crashed my xconfig twice! thank you!!!

---

### Post by 454redhawk on 2007-01-02
another that might help

[http://www.ubuntuforums.org/showthread.php?t=280683&highlight=1440x900]("http://www.ubuntuforums.org/showthread.php?t=280683&highlight=1440x900")

---

