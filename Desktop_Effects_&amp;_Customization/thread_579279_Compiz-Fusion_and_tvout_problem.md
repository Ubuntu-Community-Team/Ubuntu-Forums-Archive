---
title: "Compiz-Fusion and tvout problem"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by MrMasj on 2007-10-18
Alright I can run compiz-fusion in 7.10 without problem aslong as tvout is not enabled.
But when tvout is enabled the effects are turned off and when I try to enable them again
I get the following error "Desktop effects could not be enabled" helpful right ;)

I have an Nvidia 6600GT running with (NVidia binary X.Org driver ('new' driver)
It's a long time since I had a Linux dist installed last time, so I'm not really 100%
so I might have done a mistake in the xorg.conf there fore the reason of me posting it below.

Please give it a shot It would be fantastic if this problem could be solved
Best Regards Martin


xorg.conf
```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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
	Identifier	"Device[0]"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
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

 Section "Monitor" 
    Identifier "Monitor[1]" #TV 
    HorizSync 30-50
    VertRefresh 60 
 EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Screen[0]" 0 0
  screen 1 "screen[1]" rightof "Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device[1]" 
   	Screen 1 
   	Option          "TVOutFormat" "Composite"
   	Option          "TVStandard" "PAL-B" 
   	Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0"
EndSection

Section "screen" # TV
	Identifier	"Screen[1]"
	Device		"Device[1]"
	Defaultdepth	24
	Monitor		"Monitor[1]"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"
	EndSubSection
EndSection


Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection
```

---

