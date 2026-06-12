---
title: "[Solved] 1920x1080 on LCD TV with Jaunty"
date: 2009-06-13
forum: General Help
---

### Post by Regenpak on 2009-06-13
Maybe I didn't search good enough but I just couldn't figure outhow to get a usuable display on the VGA input of my 40" Sumsing LE40F71. The Nvidia GUI insisted on a CRT (!) with max resolution of 1024x768 instead of 1920x1080. Obviously xorg.conf needed editing as I had done in my 7.04 install but since my mobo blew up I had installed 9.04 instead, with the above results.

Putting the "old" modeline in xorg.conf resulted in the dreaded "mode not supported" message on my LCD TV. It did briefly show an image with a 4:3 aspect ratio. Not good. After searching some more I found a version of xorg.conf that looked promising, but while after rebooting I got my desktop back it was still in the old resolution. However, running "gksu nvidia-settings" now showed the 1920x1080@60 selection I needed. After saving and rebooting it proved to be persistent. The GUI still insults my LCD by calling it "CRT-0" but at least it now works.

The contents of the old xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"		"true"
EndSection

Section "Monitor"
	Identifier	"LCD TV"
	VendorName	"Sumsing"
	ModelName	"LE40F71B"
	HorizSync	60 - 70
	VertRefresh	50 - 80
	Modeline	"1920x1080@60" 138.500 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"LCD TV"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

```
After running "gksu nvidia-settings" it became:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "LCD TV"
    VendorName     "Sumsing"
    ModelName      "LE40F71B"
    HorizSync       60.0 - 70.0
    VertRefresh     50.0 - 80.0
    ModeLine       "1920x1080@60" 138.500 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       60.0 - 70.0
    VertRefresh     50.0 - 80.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "true"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "LCD TV"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
Errr... OK...

T.J.

---

