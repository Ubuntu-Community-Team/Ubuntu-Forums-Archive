---
title: "XGL + fglrx 8.40 + MR9600 on a Inspiron 8600 = freeze"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by luciphercolors on 2007-09-14
Hi everyone,

I'm trying to set up Compiz-Fusion to work on my Dell Inspiron 8600 with a 19x12 display and a mobility radeon 9600 chip. I've gotten as far as getting XGL up and running, and that's where I'm running into problems....

Here's the situation:
[LIST]
[*]Kubuntu 7.04 Feisty
[*]fglrx 8.40 off ATI's website -or- whatever version the open-source radeon driver that apt-get installs
[*]recompiled kernel, config is same as default, just recompiled it with libc++5 or something like that so that beryl would run...
[*]Mobility Radeon 9600 Pro Turbo graphics chip on a Dell Inspiron 8600 1900x1200
[/LIST]

I've read countless threads on the topic and performed what they said, I've installed XGL and gotten it to run, I've installed compiz-fusion (and before that tried beryl), I've tried the open-source ATI drivers with AIGLX. I've even recompiled my kernel with a couple extra extensions added in.

I'm at an impasse:

[b]"radeon" driver is unstable ... I get a hard lock a couple of minutes in.
"fglrx" 8.40 is stable with AIGLX, except for the occasional garbled display. fglrx + XGL is unusably slow, before it hard-locks about a minute or two in. [/b]

With these hard locks, sometimes I can SSH into the laptop and run "shutdown -r now" to restart the thing, and sometimes the mouse cursor will still move around. I can't ever hit ctrl+alt+F1 to switch to a terminal though.

I'm not going to ask how to compiz-fusion up and running, thats not something I'm too worried about and its not what this thread is about. **XGL runs like crap and is crazy unstable. How can I speed it up and make it run normal?**

I'll reply to this thread with the relevant config files.

Thanks!

---

### Post by luciphercolors on 2007-09-14
Here's the config files, as promised:

/etc/X11/xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

  # path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

# tom's additions
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	SubSection "extmod"
		Option	    "omit xfree86-dga"
	EndSubSection
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
#	Load  "v4l"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "type1"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "on"
	Option	    "MinSpeed" "0.5"
	Option	    "MaxSpeed" "100"
	Option	    "AccelFactor" "0.05"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	VendorName   "Generic"
	ModelName    "Flat Panel 1920x1200"
	HorizSync    31.5 - 90.0
	VertRefresh  60.0 - 60.0
	Gamma        1
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	ModeLine     "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	ModeLine     "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	ModeLine     "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	ModeLine     "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
	ModeLine     "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"

 #     
	Identifier   "monitor1"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

# tom's additions
#	Option      "EnablePageFlip" "true" 
#	Option      "AccelMethod" "EXA"
#	Option	
	Identifier  "ATI Mobility Radeon 9600 (fglrx)"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "MergedFB" "off"
	Option	    "Centermode" "off"
	Option	    "PseudoColorVisuals" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "VideoOverlay" "on"
	Option	    "FSAAScale" "0"
	Option	    "DRI" "true"
#	Option      "ColorTiling" "on"
	BusID       "PCI:1:0:0"
	Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Mobility Radeon 9600 (fglrx)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1920 1200
		Depth     24
		Modes    "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

/usr/bin/startxglkde.sh:
```

#!/bin/sh 
 Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
 DISPLAY=:1
 exec startkde

```

/usr/share/xsessions/xgl.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Name=KDE With XGL
Comment=Start a KDE Session with XGL
Exec=/usr/bin/startxglkde.sh
Icon=
Type=Application

```

I'm not sure what else is relevant but let me know and I'll try to post it. 

Between manually configuring the unacceptably slow sensitivity on my touchpad, numerous attempts at setting up wireless drivers (then finally giving up for ndiswrapper), fglrx headaches, beryl headaches, NTFS-write headaches, and still-to-be-troubleshooted poor sound quality headaches, I'm getting exhausted with configuring Kubuntu. And before Kubuntu, I tried linspire, mandriva, and openSuSE.... at least kubuntu has good support :-)

---

