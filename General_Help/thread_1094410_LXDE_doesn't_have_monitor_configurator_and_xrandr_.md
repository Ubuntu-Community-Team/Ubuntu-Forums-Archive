---
title: "LXDE doesn't have monitor configurator and xrandr is written in broken english"
date: 2009-03-12
forum: General Help
---

### Post by Neo_The_User on 2009-03-12
***SOLVED!*** I installed gnome-randr-applet and grandr in LXDE. works fine.
Hi. I did man xrandr and I couldn't understand it because it was written in weird english. I googled this problem but none of them really explain MY situtation.

I have 2 of the exact same displays (LCD 1440x900 Westinghouse) except one is DVI and the other is VGA. I have a heavily modified ATi 9800 PRO AGP 8X card. I am trying to configure a big desktop. I did "Virtual 2880 900" without quotes in xorg.conf but nothing happened. Any suggestions? I want my left monitor on the left, right monitor on the right, and LXDE doesn't have a graphical way to configure displays like GNOME. (i hate LXDE btw) I'm looking for 1 command I can just run that just does what I want and I know there is one. Its some magic combination of xrandr and I can't figure it out so the answer can't be RTFM.

---

### Post by Neo_The_User on 2009-03-12
I'm about to watch some movies and do more mesa development and its much easier using 2 screens at the same time. Help? I'm not a noob so speak technical if you wish. I just don't get the stupid man page. I'm using Xorg server 1.6 from git so I can't use fglrx otherwise I would. Anybody know the magic combination for dual monitors by configuring xrandr? Here is my xorg.conf file for those who might need it:

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "dri2"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  410   260	# mm
	Identifier   "Monitor0"
	VendorName   "WDE"
	ModelName    "LCM-19w4"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        Option     "AGPMode"            	"4"
        Option     "AGPFastWrite"       	"True"
        Option     "AGPSize"            	"8"
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        Option     "DMAForXv"           	"True"
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R350 [Radeon 9800 Pro]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual   2880 900
	EndSubSection
EndSection

Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection

```

The ServerFlags part is because I don't want HAL. It's just another thing that could break.

---

### Post by Neo_The_User on 2009-03-13
bump

---

### Post by Neo_The_User on 2009-03-13
***SOLVED!***

I installed 2 programs called gnome-randr-applet and and grandr. I have dependency issues since they depend on GNOME but I'm using LXDE but thaks to heindsight's help, I can cover them up.

---

