---
title: "xorg issues"
date: 2008-04-30
forum: Desktop Environments
---

### Post by whitethunder922 on 2008-04-30
I just upgraded from 7.10 to 8.04 and I can't get my resolution to stay at 1280x1024. 7.10 had some issues with this at all but with some xorg.conf hacking I was able to get it to work. The same xorg file no longer does any good. I'm running an Nvidia GeForce 7300 SE and my monitor is an IBM LCD capable of 1280x1024 max res. Here is my old working xorg.conf - any suggestions?

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
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

---

### Post by r.stiltskin on 2008-05-01
Try replacing these three sections of xorg.conf, and delete your "ServerLayout" section altogether.  Check your monitor's documentation to verify that the HorizSync and VertRefresh values are correct; change them if necessary.  Leave the rest of the file as it is.

Obviously, save a backup copy of your current xorg.conf just in case...

```
Section "Device"
    Identifier "Failsafe Device"
    Boardname "NVIDIA GeForce 7 Series"
    Busid "PCI:1:0:0"
    Driver "nv"
    Vendorname "NVIDIA"
EndSection

Section "Monitor"
    Identifier "Failsafe Monitor"
    Vendorname "Generic LCD Display"
    Modelname "LCD Panel 1280x1024"
    Horizsync 31.5-64.0
    Vertrefresh 56.0 - 65.0
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Failsafe Device"
    Monitor "Failsafe Monitor"
    Defaultdepth 24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection

EndSection
```

---

### Post by Padie on 2008-05-01
You could also try Envy....search Synaptics for "envy", and let it install and configure your Xorg file for you. Hope this helps!

---

### Post by raygj on 2008-05-01
> **Padie said:**
> You could also try Envy....search Synaptics for "envy", and let it install and configure your Xorg file for you. Hope this helps!

in 8.04 you must  install "envyng" not "envy".
IE "sudo apt-get install envyng"

---

