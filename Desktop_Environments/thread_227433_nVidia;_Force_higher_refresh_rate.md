---
title: "nVidia; Force higher refresh rate"
date: 2006-08-01
forum: Desktop Environments
---

### Post by halfvolle melk on 2006-08-01
Hi,
How can I force a higher refresh rate? Currently it's doing 1280x1024@60 and I'd like it to be something like 1280x1024@75.
I have an Iiyama Vision Master Pro 400 A701GT and should be able to do 1280x1024@87.
Sync frequency - Horizontal: 27.0-96.0kHz, Vertical: 50-160Hz.

The video card is an nVidia 6600GT running the driver from [this how-to](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia). The driver works correctly:
```
hb@eojd:~$ glxinfo | grep direct
direct rendering: Yes
```

Stuff I've tried that didn't work:
```
SubSection "Display"
		Depth		24
		Modes		"1280x1024_75" "1024x768" "832x624" "800x600" "720x400" "640x480"
```
```
modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
```
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	27-96
	VertRefresh	75-160
```
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	27-100
	VertRefresh	50-160
```
```
Section "Device"
  identifier "NVIDIA Corporation NV43 [GeForce 6600 GT]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
  Option "ModeValidation" "NoEdidModes"
EndSection
```
/var/log/Xorg.0.log responds with
```
(WW) NVIDIA(0): No valid modes for "1280x1024@75"; removing.
```

I'm out of ideas. Does anyone have any other ideas?

---

### Post by l.tambiah on 2006-08-01
You could try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by halfvolle melk on 2006-08-01
Thanks for your suggestion but all that does, I think, is create a generic xorg.conf that needs editing. I tried it anyway and unfortunately didn't work. Still, thanks for for the help though :)

Does anyone know if picking another driver version might fix this?

---

### Post by halfvolle melk on 2006-08-03
Anyone know what I'm doing wrong? Or, if you don't have this issue, what driver version are you using?

Thanks

---

### Post by bmonkey on 2006-08-03
It has to do with ur monitor - if ur monitor doesnt support 75hz then ubuntu will not show u that option, check that your monitor is being picked up properly by ubuntu.

---

### Post by halfvolle melk on 2006-08-03
When I do this (KDE):
system settings -> display -> hardware -> configure -> manufacturer -> Iiyama A701GT, Vision master pro400. Apply returns
> The selected driver and monitor configuration can not be safely tested on this computer
and xorg.conf gets stuffed with this
```
Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Iiyama"
  modelname "Iiyama A701GT, VisionMasterPro 400"
  HorizSync 27.0-96.0
  VertRefresh 50.0-160.0
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
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
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
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@75" "1280x1024@85" "1400x1050@60" "1280x960@85" "1400x1050@75" "1280x960@60" "1600x1200@65" "1280x1024@75" "1600x1200@60" "1280x854" "1600x1200@75" "1152x768@54" "1600x1200@70" "1152x864@75" "1792x1344@60" "1024x768@43" "1856x1392@60" "1024x768@60" "1920x1440@60" "1024x768@70" "2048x1536@60" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection
```
but only picks up 1280x1024@60. With my ATi card I did get it to play nice but I can't remember at what frequency I put it :(

Thanks for your input, I'll mess around with different frequencies some more.

---

### Post by bmonkey on 2006-08-03
> 
Section "Screen"
  **Identifier "Default Screen"**
  Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
  **Monitor "Generic Monitor"**
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@75" "1280x1024@85" "1400x1050@60" "1280x960@85" "1400x1050@75" "1280x960@60" "1600x1200@65" "1280x1024@75" "1600x1200@60" "1280x854" "1600x1200@75" "1152x768@54" "1600x1200@70" "1152x864@75" "1792x1344@60" "1024x768@43" "1856x1392@60" "1024x768@60" "1920x1440@60" "1024x768@70" "2048x1536@60" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection


Try get the right drivers for your screen - a friend had this problem and when he managed to get his screen detected properly his resolution problems were fixed (aswell as frequency)

---

### Post by halfvolle melk on 2006-08-03
You mean drivers in addition to the nVidia driver?

---

### Post by halfvolle melk on 2006-08-03
w00t! Fixed!
It's now on 85 (which also didn't work earlier without the below options), haven't tried 75 yet. Adding 2 options to the device section made it work:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option         "ModeValidation" "NoEdidModes"
        Option         "UseEDID" "FALSE"
```
The entire xorg.conf:
```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option         "ModeValidation" "NoEdidModes"
        Option         "UseEDID" "FALSE"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       27-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024_85" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```
Edit: I think the "UseEDID" "FALSE" is what does the trick.

---

