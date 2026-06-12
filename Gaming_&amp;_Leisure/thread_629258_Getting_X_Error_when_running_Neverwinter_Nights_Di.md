---
title: "Getting X Error when running Neverwinter Nights Diamond (Native)"
date: 2007-12-02
forum: Gaming &amp; Leisure
---

### Post by TremerePuck on 2007-12-02
I'm getting the following error when I try to run NWN:

```
puck@puck:~/nwn$ ./nwn
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x187
  Serial number of failed request:  133
  Current serial number in output stream:  13
```

Just in case here is my xorg.conf:

```
Section "ServerLayout"
	Identifier	"Layout0"
  screen 0 "Screen0" 0 0
	Inputdevice	"Keyboard0"	"CoreKeyboard"
	Inputdevice	"Mouse0"	"CorePointer"
	Inputdevice	"Wiimote"	"AlwaysCore"
EndSection

Section "Files"
	Rgbpath		"/usr/lib/X11/rgb"
EndSection

Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier	"Wiimote"
	Driver		"evdev"
	Option		"Name"	"Nintendo Wiimote"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection

Section "Monitor"
	
	# HorizSync source: edid, VertRefresh source: edid
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"HP MX70"
	Horizsync	30.0	-	70.0
	Vertrefresh	47.0	-	120.0
  modeline  "1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce FX 5200"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"SecondMonitorHorizSync"	"30-85"
	Option		"SecondMonitorVertRefresh"	"50-120"
	Option		"TwinView"	"1"
	Option		"metamodes"	"CRT-0: 1280x1024, CRT-1: 1280x1024; CRT-0: NULL, CRT-1: 1280x1024; CRT-0: NULL, CRT-1: 1600x1200 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

```

Any and all help is appreciated.

---

### Post by TremerePuck on 2007-12-03
Using the installer from [http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259) I got a slightly different error:

```
puck@puck:~/nwn$ ./nwn
X11: Unknown xsym, sym = 0x1008ff11
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x187
  Serial number of failed request:  108
  Current serial number in output stream:  110

```

---

### Post by TremerePuck on 2007-12-03
I had to use the nvidia drivers installer to uninstall the drivers then reinstall them. Apparently part of a legacy driver I had before was still creeping around causing trouble. But it works great now!

---

### Post by WSmart on 2013-02-11
Adding to this old thread a solution I found to this issue as searching the error gave me this post on top.

On my system the driver was working correctly but NWN would not launch.  Apparently this was caused by the in game resolution being set higher then my desktop resolution.   I edited nwn.ini to lower the game resolution and the game launched normally.

Thanks all.

Be real. be sober.

---

