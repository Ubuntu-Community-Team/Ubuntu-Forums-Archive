---
title: "wide screen in ubuntu"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Abadon on 2006-07-21
Hi there,

I have a wide screen monitor dell 2005FPW which is 1680x1250. The bigest resolution in ubuntu is 1024x768. Does anyone know how to change that resolution. Any help will be greatly appreciated

---

### Post by ahaslam on 2006-07-21
I assume that you're using the generic 'vesa' graphics driver, to confirm check your xorg.conf (/etc/X11/xorg.conf), look at the *Section "Device"*. If it shows that you're using the 'vesa' driver, you'll need to install drivers for your specific hardware to enable higher resolutions & better performance. If you want help with installing the correct drivers, let us know what graphics hardware you've got.

Tony.

PS. If you're using the correct drivers, it may just be a case of adding resolutions to the screen section of xorg.conf.

---

### Post by Brando569 on 2006-07-21
just edit your xorg.conf, i use 1152x864 :D

---

### Post by Abadon on 2006-07-21
It looks like its Nvidia CK804 Alsa capture device. Thanks

---

### Post by shawnrgr on 2006-07-21
if you install and activate the nvidia/ati driver, it should auto detect your monitor as widescreen and set it up by itself. if not, after the nvidia/ati driver is installed, edit your xorg.conf. change all the resolutions you find to the one you want to use. while your there you can also set the proper h&v sync rates as mine were a little off. the just [ctrl+alt+backspace] to restart gnome/gdm without restart the computer itself. everything should be fine then.

---

### Post by rbprogrammer on 2006-07-21
i had the same exact problem with the same resolution... so i posted a thread, and i was told to check out the package 915resolution from the backports through adept and then i changed that X11 file to the resolution 1680x1050 (or whatever) and it worked the next time i booted up

---

### Post by blitzd on 2006-07-22
> **Abadon said:**
> Hi there,

I have a wide screen monitor dell 2005FPW which is 1680x1250. The bigest resolution in ubuntu is 1024x768. Does anyone know how to change that resolution. Any help will be greatly appreciated
Here is an example of a setup for a 2005FPW monitor...

```
Section "Module"
  Load         "freetype"
  Load         "type1"
  Load         "dbe"
  Load         "glx"
  Load         "extmod"
  Load         "v4l"
EndSection

Section "Monitor"
  DisplaySize  430 270
  HorizSync    30-83
  Identifier   "Monitor[0]"
  ModelName    "2005FPW (ANALOG)"
  Option       "DPMS"
  VendorName   "DELL"
  VertRefresh  56-75
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1680x1050" 181.61 1680 1792 1976 2272 1050 1051 1054 1095
  Modeline 	"1680x1050" 178.96 1680 1792 1976 2272 1050 1051 1054 1094
  Modeline 	"1680x1050" 176.48 1680 1792 1976 2272 1050 1051 1054 1094
  Modeline 	"1600x1024" 168.40 1600 1704 1880 2160 1024 1025 1028 1068
  Modeline 	"1600x1024" 165.94 1600 1704 1880 2160 1024 1025 1028 1067
  Modeline 	"1600x1024" 163.64 1600 1704 1880 2160 1024 1025 1028 1067
  Modeline 	"1600x1000" 164.46 1600 1704 1880 2160 1000 1001 1004 1043
  Modeline 	"1600x1000" 162.05 1600 1704 1880 2160 1000 1001 1004 1042
  Modeline 	"1600x1000" 159.80 1600 1704 1880 2160 1000 1001 1004 1042
  Modeline 	"1400x1050" 151.56 1400 1496 1648 1896 1050 1051 1054 1095
  Modeline 	"1400x1050" 149.34 1400 1496 1648 1896 1050 1051 1054 1094
  Modeline 	"1400x1050" 147.27 1400 1496 1648 1896 1050 1051 1054 1094
  Modeline 	"1280x1024" 134.72 1280 1368 1504 1728 1024 1025 1028 1068
  Modeline 	"1280x1024" 132.75 1280 1368 1504 1728 1024 1025 1028 1067
  Modeline 	"1280x1024" 130.91 1280 1368 1504 1728 1024 1025 1028 1067
  Modeline 	"1440x900" 132.71 1440 1536 1688 1936 900 901 904 939
  Modeline 	"1440x900" 130.75 1440 1536 1688 1936 900 901 904 938
  Modeline 	"1440x900" 128.93 1440 1536 1688 1936 900 901 904 938
  Modeline 	"1280x960" 126.27 1280 1368 1504 1728 960 961 964 1001
  Modeline 	"1280x960" 124.54 1280 1368 1504 1728 960 961 964 1001
  Modeline 	"1280x960" 122.69 1280 1368 1504 1728 960 961 964 1000
  Modeline 	"1366x768" 106.19 1368 1448 1592 1816 768 769 772 801
  Modeline 	"1366x768" 104.73 1368 1448 1592 1816 768 769 772 801
  Modeline 	"1366x768" 103.15 1368 1448 1592 1816 768 769 772 800
  Modeline 	"1280x800" 104.35 1280 1360 1496 1712 800 801 804 835
  Modeline 	"1280x800" 102.80 1280 1360 1496 1712 800 801 804 834
  Modeline 	"1280x800" 101.37 1280 1360 1496 1712 800 801 804 834
  Modeline 	"1152x864" 102.08 1152 1224 1352 1552 864 865 868 901
  Modeline 	"1152x864" 99.64 1152 1224 1344 1536 864 865 868 901
  Modeline 	"1152x864" 98.15 1152 1224 1344 1536 864 865 868 900
  Modeline 	"1280x768" 99.17 1280 1352 1488 1696 768 769 772 801
  Modeline 	"1280x768" 97.81 1280 1352 1488 1696 768 769 772 801
  Modeline 	"1280x768" 96.33 1280 1352 1488 1696 768 769 772 800
  Modeline 	"1024x768" 79.52 1024 1080 1192 1360 768 769 772 801
  Modeline 	"1024x768" 78.43 1024 1080 1192 1360 768 769 772 801
  Modeline 	"1024x768" 77.25 1024 1080 1192 1360 768 769 772 800
  Modeline 	"1280x600" 76.04 1280 1336 1472 1664 600 601 604 626
  Modeline 	"1280x600" 75.00 1280 1336 1472 1664 600 601 604 626
  Modeline 	"1280x600" 73.84 1280 1336 1472 1664 600 601 604 625
  Modeline 	"1024x600" 61.42 1024 1080 1184 1344 600 601 604 626
  Modeline 	"1024x600" 59.86 1024 1072 1176 1328 600 601 604 626
  Modeline 	"1024x600" 58.93 1024 1072 1176 1328 600 601 604 625
  Modeline 	"800x600" 47.53 800 840 920 1040 600 601 604 626
  Modeline 	"800x600" 46.87 800 840 920 1040 600 601 604 626
  Modeline 	"800x600" 46.15 800 840 920 1040 600 601 604 625
  Modeline 	"768x576" 43.52 768 800 880 992 576 577 580 601
  Modeline 	"768x576" 42.93 768 800 880 992 576 577 580 601
  Modeline 	"768x576" 42.26 768 800 880 992 576 577 580 600
  Modeline 	"640x480" 29.84 640 664 728 816 480 481 484 501
  Modeline 	"640x480" 29.43 640 664 728 816 480 481 484 501
  Modeline 	"640x480" 29.03 640 664 728 816 480 481 484 501
EndSection

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "Device"
  BoardName    "Quadro FX 350M"
  BusID        "1:0:0"
  Driver       "nvidia"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "NVidia"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection
```

That has every resolution that is possible on a 2005FPW. Hope it helps!

---

### Post by city-17 on 2006-09-11
I have a Dell 2005fpw with a resolution of 1680x1050. I had to install the nvidia driver and add a Modeline in the section "Monitor" of xorg.conf.

Take a look at my xorg configuration, hope this helps.

```
Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
        HorizSync       30-83
        VertRefresh     60
        Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41.1 [GeForce 6800]"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

```

---

### Post by bcursor on 2006-10-14
I have a ati card in Toshiba Notebook. When I try with open-source ati drivers the wide screen doesnt work. I have installed fglrx drivers then that works. But now I can only choose 1280x800 resolution

---

