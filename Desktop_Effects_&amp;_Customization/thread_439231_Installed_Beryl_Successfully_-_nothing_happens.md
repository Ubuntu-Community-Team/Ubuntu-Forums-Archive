---
title: "Installed Beryl Successfully - nothing happens"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by StormJosh on 2007-05-10
Hey everyone. This is my first go with Ubuntu/Beryl, so please bear with me :)

That being said, I've installed Beryl, seemingly successful, I have the manager in the upper right hand corner and I can adjust all the effects and what not.

My problem is that I can't do ANYTHING with Beryl. I can't access any of the features such as the desktop cube or the wobbly windows or anything. It's all enabled. I've tried CTRL-ALT-Right, CTRL-ALT-Left Click and nothing happens. 

If it helps, my video card is: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)

Anyone have any ideas?

---

### Post by DarkN00b on 2007-05-10
First, make sure you have direct rendering enabled. Type ```
glxinfo | grep direct
``` into a terminal and hit enter. If you get ```
direct rendering: Yes
```
then type ```
beryl
``` or ```
beryl-manager
``` into a terminal and hit enter. Beryl should start then.

---

### Post by StormJosh on 2007-05-10
Thanks for the reply. When I enter glxinfo | grep direct I get "yes" as a response.

However, when I enter beryl into the terminal, here is what I get:
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...
[B]
Checking for XComposite extension               : failed

No composite extension[/B]

The bolded parts obviously concern me. Anyone know how to fix this?

---

### Post by orb9220 on 2007-05-10
In your xorg.conf file you have to check and see if you have these lines in bold if not add them to yours.

> Section "Monitor"
    Identifier     "A75f"
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	**Option 		"AllowGLXWithComposite" "true"**
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
      [B]  Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"[/B]
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

[B]Section "Extensions"
          Option  "Composite" "Enable"
EndSection[/B]

---

