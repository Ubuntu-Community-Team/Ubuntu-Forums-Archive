---
title: "NVIDIA Twinview problems."
date: 2005-05-01
forum: Desktop Environments
---

### Post by olnir on 2005-05-01
I pretty new to Linux/Ubuntu.

I have got twinview to work on my Geforce Ti4400, but with twinview enabled the damn thing wont restart or shut down. The screen just goes blank and the computer hangs. I can not restart X.

Could somebody please help me try to figure this out. I love Ubuntu and would really like to stick with it, but this shutdown problem is slowly killing my filesystem. 

Here is my xorg.conf file.

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"is"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Driver "nvidia"
	Option "NvAGP" "1"
	Option "DigitalVibrance" "0"
	Option "TransparentIndex" "0"
	Option "CursorShadowAlpha" "64"
	Option "CursorShadowXOffse" "4"
	Option "CursorShadowYOffset" "2"
	Option "IgnoreDisplayDevices" "CRT,TV"
	Option "NoLogo" "TRUE"
	Option "CursorShadow" "TRUE"
	Option "Twinview" "TRUE"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1280x1024 , 800x600"
	Option "ConnectedMonitor" "CRT , TV"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard" "PAL-B"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option "MonitorHorizSync" "30-96"
	Option "MonitorVertRefresh" "47-150"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

