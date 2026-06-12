---
title: "[SOLVED] xrandr will not work (Gutsy, ATI Radeon x1400, fglrx)"
date: 2007-10-21
forum: Desktop Environments
---

### Post by midden on 2007-10-21
Hi all,

I am trying to get dual head to work after a (in retrospect hasty) Feisty to Gutsy upgrade. I realize that the old Xinerama methods I used in Feisty will not work now, so I am attempting to use the xrandr methods (as suggested in post # 12 [here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574426&page=2")). However, xrandr does not appear to work under my current setup (perhaps an Xgl problem?). Do you have any suggestions?

Here is the output from xrandr:

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

output from fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```

And finally, in case it will help, the relevant bits from my current xorg.conf file. I commented out the Sync and Refresh lines in the Monitor Section and the Modes line in the Display Subsection; however, these changes do not alter the output from xrandr.

```

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#	HorizSync	28-70
#	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
#		Modes		"1400x1050" "1280x1024" "1024x768" "800x600"
        Depth 24
        Virtual     2680 1050
        ViewPort 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

EndSection
```

(I did see a similar question posted [here]("http://ubuntuforums.org/showthread.php?t=571366&highlight=xrandr") but there were no comments and the forum is now closed.)

This is installed on a Thinkpad T60 (2613HKU)

Thanks for your help.

---

### Post by Yv12345vY on 2007-10-22
Same thing I'm seeing.  No idea what to do with it though.

---

### Post by midden on 2007-10-22
I still have not managed to get xrandr to work. However, I have enabled the large desktop using Xinerama (I posted an excerpt from my xorg.conf in case this will help others). This involved adding my specific external monitor using the System/Administration/Screens and Graphics gui and then editing xorg.conf by hand.

I do miss the two independent desktops I had in Feisty. I can suffer through the big desktop but would rather do my suffering using Xrandr. Can anyone help me modify my xorg.conf such that Xrandr will work on my Radeon Mobility x1400? Thanks for your help


```

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
        modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "Default Screen" 0 0
        screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "on"
        Option "DesktopSetup" "horizontal"
        Option "Mode2" "1400x1050,1280x1024"
        Option "PairModes" "1400x1050+1400x1050,1280x1024+1280+1024"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
        Viewport 0 0
		Modes   "1400x1050" "1280x1024"
        #Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"1024x768@85"	"1600x1200@60"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 710N/177N/CX711N/CX701N"
	Horizsync	30-81
	Vertrefresh	56-85
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
        modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        #modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
        #modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        #modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        #modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"true"
        Option      "AIGLX" "off"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection
```

---

### Post by midden on 2007-10-23
OK, I started messing around with my xorg.conf in the spirit of "even a blind hog finds an acorn once in a while." In the process, I managed to get xrandr AND dual desktops (i.e., two independent desktops like I had under Feisty). I am attaching my entire xorg.conf in case it helps others who are struggling to get the fglrx driver to work with Gutsy.

Because I really don't know what I am doing, I am sure there are some superfluous lines in the file. If anybody out there has the time, please let me know what lines can be removed. Thanks for your help. 

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
    Option "VideoOverlay" "on"
    Option "OpenGLOverlay" "on"
    Option "DesktopSetup" "horizontal"
    Option "Mode2" "1400x1050 1280x1024"
    Option "PairModes" "1400x1050+1400x1050,1280x1024+1280x1024"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
        Viewport 0 0
        Modes "1400x1050 1280x1024"
        #Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"1024x768@85"	"1600x1200@60"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 710N/177N/CX711N/CX701N"
	Horizsync	30-81
	Vertrefresh	56-85
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  #modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  #modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  #modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"false"
    Option      "AIGLX" "off"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
    Option "RandR" "Enable"
EndSection
```

---

### Post by Whoopie on 2007-10-23
btw, fglrx doesn't support the randr extension, just the radeon OSS driver.

---

### Post by midden on 2007-10-23
Thanks. I took out that line and everything works fine, as you suggested.

---

### Post by cow_racer on 2007-10-25
It does.  I just tested xrandr on my laptop with ati x1400.

I can change resolution using xrandr command.

Now, i just wonder how to switch monitors from internal to external, and back again.

Just checked Xorg log and it said:
RandR enabled.

---

### Post by CAsurfer on 2008-01-26
midden, the final xorg.conf file you posted is quite long. Can you make clear which part of it concerns enabling screen rotation?

---

### Post by midden on 2008-01-26
I believe the critical bits are:

Section "ServerFlags"
    Option		"Xinerama"	"false"
    Option      "AIGLX" "off"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection


Basically, I think that xrandr does not work with Xinerama, so you need to turn it off. Let me know what you find.

---

### Post by CAsurfer on 2008-01-26
I just added those options, but to no avail.

To clarify my setup, I'm running Gutsy (7.10) AMD64, with an ATI card with fglrx, and with compiz running. I'm trying to rotate my screen, and my Googling suggests xrandr to be my best bet. But when I try a command like "xrandr -o left", I get the same problem midden got.

My current xorg.conf is below.

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
#	Load		"extmod"
#	Load		"randr"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerFlags"
	Option "Xinerama" "false"
	Option "AIGLX" "off"
EndSection

```


EDIT: there's a Launchpad bug report addressing the issue here: [https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/164125](https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/164125)

---

