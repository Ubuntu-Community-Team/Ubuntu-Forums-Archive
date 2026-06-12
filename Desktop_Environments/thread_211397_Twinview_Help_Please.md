---
title: "Twinview Help Please"
date: 2006-07-08
forum: Desktop Environments
---

### Post by MarkJ4322 on 2006-07-08
Hello all - just started with Ubuntu today with no previous Linux experience so please be kind :)

I've managed to get twinview working but my monitors are around the wrong way.

My normal setup is an LCD as a primary and a CRT to the right of that monitor that will act as a secondary. What I currently have in ubuntu is the CRT "right" monitor as a primary, and my LCD to the right.

So what I need is to swap primary monitors.. how do i do it?

Here's my (messy) xorg.conf - Thanks for any suggestions!
 

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
Driver		"nvidia"
BusID		"PCI:2:0:0"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 6600 GT"
Option "NvAGP" "2"
Option "NoLogo" "1"
Option "RenderAccel" "0"
Option "CursorShadow" "1"
Option "Coolbits" "1"
Option "ConnectedMonitor" "crt, dfp"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "FlipPrimary" "true"
Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
Option "SecondMonitorHorizSync" "31-82"
Option "SecondMonitorVertRefresh" "56-76"
# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-97
	VertRefresh	43-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Viewport 0 0
	Depth 24
	Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
Identifier "TwinView Configuration"
Screen 0 "Default Screen" 0 0
InputDevice "Configured Mouse"
InputDevice "Generic Keyboard"
Option "Xinerama" "Off"
InputDevice     "stylus" "SendCoreEvents"
InputDevice     "cursor" "SendCoreEvents"
InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by orb9220 on 2006-07-08
In option:

Option "ConnectedMonitor" "crt, dfp"

Chnge the order and see if that helps

---

### Post by orb9220 on 2006-07-08
or 

Option "FlipPrimary" "true"

change to false ?

Just guessing

---

### Post by MarkJ4322 on 2006-07-08
Thanks for your suggestions - but unfortunately neither worked.

---

### Post by autocrosser on 2006-07-08
What you need to do is define your monitors--take a look at my xorg.conf (also with TwinView) I'll include only the important sections--- The "trick" is to make sure that Xorg "knows" which monitor is which----

Section "Device"
    Identifier  "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
        #Option      "NvAgp"                     "1"
        Option      "TwinView"                  "true"
        Option      "MetaModes"     "1280x1024,1280x1024;1280x1024,NULL;1024x768,1024x768;800x600,800x600"
        Option      "TwinViewOrientation"       "RightOf"
        Option      "NoLogo"                    "false"
        Option      "RenderAccel"               "true"
        Option      "Backingstore"              "true"
        Option      "RandRRotation"             "true"

EndSection

Section "Monitor"
        DisplaySize     376.32  301.056
    Identifier    "Monitor1"
        ModelName       "VL1918"
        VendorName      "Princeton"
        HorizSync       31.0 - 79.0
        VertRefresh     60.0 - 70.0
    Option        "DPMS"
EndSection

Section "Monitor"
        DisplaySize     376  301
    Identifier    "Monitor0"
        ModelName       "AL1916"
        VendorName      "Acer"
        HorizSync       31.0 - 81.0
        VertRefresh     56.0 - 75.0
    Option        "DPMS"
EndSection

    Section "Screen"
        Identifier  "Screen0"
        Device      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor     "Monitor0"
        DefaultDepth 24
        Subsection "Display"
            Depth       24
            Modes       "1280x1024" "1024x768" "800x600" 
        EndSubsection
    EndSection

    Section "Screen"
        Identifier  "Screen1"
        Device      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor     "Monitor1"
        DefaultDepth 24
        Subsection "Display"
            Depth       24
            Modes       "1280x1024" "1024x768" "800x600" 
        EndSubsection
    EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen         0 "Screen0" 
    Screen         1 "Screen1" rightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection


You will need the specs on your monitors--look at you owner's manuals or go online--DisplaySize is in mm--

Hope this helps you---

---

