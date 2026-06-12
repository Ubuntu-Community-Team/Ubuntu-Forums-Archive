---
title: "How to add a modeline."
date: 2011-08-08
forum: Desktop Environments
---

### Post by Housemd on 2011-08-08
Solved


Hi,
Just install ubuntu but there is a problem of overscan.
It happened in the past too,I've found a way to solve the problem by adding this modeline:

"1920x1080_60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

My only question is,How?How can I add the modeline to xorg.conf?I tried to use sudo gedit /etc/X11/xorg.conf to do so but the file was empty and I didn't know where to start.
Can I add the modeline by the xrandr command?

Sorry for bad english and organization.

Thanks

---

### Post by Lampi on 2011-08-08
If you use the proprietary driver (nvidia or fglrx) you can set overscan compensation in the driver control center (nvidia-settings or amdcccle)

---

### Post by Housemd on 2011-08-08
Thanks for replying.I use an ATI driver with my hd 4650.It seems that the driver doesn't have any option for overscan.

---

### Post by Lampi on 2011-08-08
[Ati HD3600+karmic MINIMAL - under/over-scan HOW]("http://ubuntuforums.org/showpost.php?p=8611121&postcount=2")

---

### Post by realzippy on 2011-08-08
*Can I add the modeline by the xrandr command?*
...sure.
[http://ubuntuforums.org/showpost.php?p=7063407&postcount=3](http://ubuntuforums.org/showpost.php?p=7063407&postcount=3)

To make it permanent I would prefer /etc/gdm/Init/Default.....

---

### Post by Housemd on 2011-08-08
HI thanks for the links.
I follow all the steps but I still have the overscan.

xrandr --newmode "1920x1080_60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

xrandr --addmode HDMI-0 1920x1080_60.00

xrandr --output HDMI-0 --mode 1920x1080_60.00

I was using the resolution of 1680x1050 and I reboot to the overscaned 1920x1080 one.

I had this problem before.I remember editing the xorg.conf to slove the problem.

Maybe the command auto-fixed the modeline I typed in?I'm not sure.

Many Thanks

---

### Post by Housemd on 2011-08-08
My current xorg.conf:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "dri2"
	Load  "record"
	Load  "dbe"
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
	#DisplaySize	  480   270	# mm
	Identifier   "Monitor0"
	VendorName   "VSC"
	ModelName    "VX2260WM"
	HorizSync    15.0 - 82.0
	VertRefresh  50.0 - 75.0
	Modeline "1920x1080-60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
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
        #Option     "ClockGating"        	# [<bool>]
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
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "radeon"
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
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "1920x1080-60.00"
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
	EndSubSection
EndSection

---

### Post by realzippy on 2011-08-08
1. Did you check your monitor's menu for overscan options?
2. You are using the free ati driver,so,where does your xorg.conf come from?
3. What happened after:
   *xrandr --output HDMI-0 --mode 1920x1080_60.00*
4. Have you ever tried the non free ati (catalyst) driver ?
5. Which Ubuntu version ?

---

### Post by Housemd on 2011-08-08
1. Did you check your monitor's menu for overscan options?
Yes,only thing close is "auto adjust".but It does work.
2. You are using the free ati driver,so,where does your xorg.conf come from?
Sorry for my superficial ubuntu knowledge.I use "Xorg :1 -configure" to create one and copy everything with "sudo gedit /etc/X11/xorg.conf"
3. What happened after:
xrandr --output HDMI-0 --mode 1920x1080_60.00
I was using 1680X1050 before I type in the command.It turned to the overscaned 1920x1080 after.
4. Have you ever tried the non free ati (catalyst) driver ?
Do you mean the offical ati driver?I am installing one,hope it can work out.
5. Which Ubuntu version ?
Is this what the problem is about?I use elementary os and it was based on ubuntu 10.10

---

### Post by Lampi on 2011-08-08
> Is this what the problem is about?I use elementary os and it was based on ubuntu 10.10
Yes, you didn't use the proprietary driver (= catalyst = fglrx)

Follow this howto to install fglrx:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Then open amdcccle in administrative mode (there's a menu point for that) - then move the slider as explained in [Ati HD3600+karmic MINIMAL - under/over-scan HOW]("http://ubuntuforums.org/showpost.php?p=8611121&postcount=2") and you're DONE - it's as simple as that... it will write a xorg.conf with overscan compensation.

---

### Post by Housemd on 2011-08-09
Fooling around with the setting and somehow I got it worked.
I turned the monitor output from HDMI AV to HDMI PC and I got a perfect 1920x1080 resolution.
I think the problem is my monitor can't receive the right signal from my pc.
Modeline can fix the problem but changing the signal,but the resulted resolution may have a little flaw.

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

