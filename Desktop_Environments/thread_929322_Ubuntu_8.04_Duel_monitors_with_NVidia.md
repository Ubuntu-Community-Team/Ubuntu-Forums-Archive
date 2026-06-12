---
title: "Ubuntu 8.04 Duel monitors with NVidia"
date: 2008-09-24
forum: Desktop Environments
---

### Post by ali_williams on 2008-09-24
Hey guys I am trying to do the whole duel monitors thing with a GeForce 7300 SE, and a HP LP2065 and HP 2035 and its just not working. This is what my xorg.conf looks like and yes i know it looks like a bloody mess(see below). The issue is that i can not get the nvidia driver to work at all i reboot my icons are missing and the backgrounds are missing. I need to know what to do. Anyway the xorg.conf is below any one that can help it would be great!! :D

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP LP2065"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1920 1440
        Depth       24
        Modes      "800x600@85" "800x600@60" "800x600@75" "832x624@75" "800x600@72" "1024x768@85" "800x600@56" "1024x768@75" "640x480@85" "1024x768@70" "640x480@75" "1024x768@60" "640x480@72" "1152x864@75" "640x480@60" "1280x1024@75" "1280x960@60" "1280x960@85" "1280x1024@85" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1600x1200@75" "1600x1200@70" "1792x1344@60" "1856x1392@60" "1920x1440@60"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1600x1200@65 +0+0, DFP: nvidia-auto-select +1600+0; CRT: 800x600@85 +0+0, DFP: nvidia-auto-select +800+0; CRT: 800x600@60 +0+0, DFP: nvidia-auto-select +800+0; CRT: 800x600@75 +0+0, DFP: nvidia-auto-select +800+0; CRT: 832x624@75 +0+0, DFP: nvidia-auto-select +832+0; CRT: 800x600@72 +0+0, DFP: nvidia-auto-select +800+0; CRT: 1024x768@85 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 800x600@56 +0+0, DFP: nvidia-auto-select +800+0; CRT: 1024x768@75 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 640x480@85 +0+0, DFP: nvidia-auto-select +640+0; CRT: 1024x768@70 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 640x480@75 +0+0, DFP: nvidia-auto-select +640+0; CRT: 1024x768@60 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 640x480@72 +0+0, DFP: nvidia-auto-select +640+0; CRT: 1152x864@75 +0+0, DFP: nvidia-auto-select +1152+0; CRT: 640x480@60 +0+0, DFP: nvidia-auto-select +640+0"
EndSection

---

### Post by lian1238 on 2008-09-25
You could try installing nvidia-settings and configure using that if you aren't already.

---

### Post by AnRkey on 2008-09-25
sudo apt-get install envyng envyng-gtk
sudo envyng-gtk
no need to first remove old drivers, envy will do that for you. Upgrade to latest drivers and reboot.

Then run sudo nvidia-settings and use it to detect the screens. Do a test and save your settings.

Let us know if this worked out.

R

---

### Post by j.miller565 on 2008-09-25
Should be easy enough to do in gksu nvidia-settings once you've installed the nvidia driver. Do you want to clone the monitor or make it an extended desktop?

---

### Post by issih on 2008-09-25
Annoyingly pedantic I know, but duel means a fight, dual means two of something. Its a pet bugbear of mine sorry :)

I second the idea of giving envy ng a whirl, once the nvidia driver is working correctly you should be able to enable dual monitor usage simply using the nvidia settings gui.

Hope that helps

---

### Post by ali_williams on 2008-09-25
> **AnRkey said:**
> sudo apt-get install envyng envyng-gtk
sudo envyng-gtk
no need to first remove old drivers, envy will do that for you. Upgrade to latest drivers and reboot.

Then run sudo nvidia-settings and use it to detect the screens. Do a test and save your settings.

Let us know if this worked out.

R
according to ubuntu it couldn't find a envyng package
"E: Couldn't find package envyng"

---

### Post by j.miller565 on 2008-09-26
ooh yea you can get EnvyNG from this site, it'll tell you how to install it too:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ali_williams on 2008-09-26
Well i ran though it and it added the Nvidia X Server Settings on the box and when I went into that area it says no nvidia driver is loaded. It also screwed up my screen rez to where I am at 800x600. Here is what it did to the tail end of my xorg.conf

> Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP LP2065 Flat Panel Monitor"
	Horizsync	30.0-92.0
	Vertrefresh	48.0-85.0
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
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1440
		Modes		"1600x1200@70"	"1792x1344@60"	"1600x1200@60"	"1856x1392@60"	"1600x1200@65"	"1920x1440@60"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x1024@85"	"1280x960@85"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
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
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection



As you can see it should be using my monitor at 1600x1200@70 but its only doing 800x600. I am going to try to tinker with the xorg to get my screen rez back up to 1600x1200 but can anyone tell me why it doesnt see a nvidia driver on the "Nvidia X Server Settings" app? because the xorg.conf says 	"Driver		"nvidia"" which i thought it meant I was using the right driver.

---

### Post by lian1238 on 2008-09-26
I think you should reinstall the latest nvidia drivers downloaded from Nvidia.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Let the installer configure X for you. If you don't want to install a new one, you could try nvidia-xconfig.

Thinking of which, I'm going to update my drivers too. :)

---

