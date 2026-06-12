---
title: "DUAL SCREEN problem!!!!!"
date: 2007-05-03
forum: Desktop Environments
---

### Post by mdowling86 on 2007-05-03
i have a nvidia gt 7300 

first time ubuntu user i started 4 days ago :-)

i have set up almost everything in the nvidia settings (gksudo nvidia-settings)

ok so i have got my two screens set up as "separate x screens" best way i have found to set up so i can play movies on one and games or documents on the other.  and i can move the icons from one screen to the other. BUT i cant find a way to move open folders or programs from one screen to the other that is really my only problem with the system.


Can anyone help me?

---

### Post by mojoman on 2007-05-03
I'm not sure how you set it up but if you're using nVidia I wouyld recommend using TwinView. It gives you a desktop stretching over two monitors (or one monitor and one TV, or one monitor and on projector, etc) and lets you freely move your applications between the two screen. I've used it on Ubuntu Dapper and now I'm using it on Xubuntu Feisty and it works great, though the Gnome windowmanager (Metacity) requires a a patch to always open the applications on the screen that the mouse curser is on.

Have a look at this thread for a  tvinwiev howto

[http://ubuntuforums.org/showthread.php?t=301946](http://ubuntuforums.org/showthread.php?t=301946)

Also, a thread on the metacity patch is here

[http://ubuntuforums.org/showthread.php?t=242502](http://ubuntuforums.org/showthread.php?t=242502)

Get back if this doesn't solve it.

/mojoman

---

### Post by orb9220 on 2007-05-03
Yes you must have twinview to drag apps back and forth. seprate screens do not support across monitors.

Here is mine as an example

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
	Option 		"AllowGLXWithComposite" "true"
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
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
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

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

### Post by Nythain on 2007-05-04
you dont need twinview to move windows across monitors... select seperate x screens in nvidia-settings and check the xinerama box... will give you two screens, so you can maxize stuff on one, and still let you transfer between the two... two displays is considerably more resource intensive from what i've noticed though, so i hope your machine is up for it... mine lags and chops trying to watch a movie and surft teh web on seperate monitors... but overall it works.

the specific edit to your xorg.conf would be
Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

---

### Post by orb9220 on 2007-05-04
Thats wierd since my nvidia-settings are for Twinview. And I can drag across screens and if I maximize in only maxs to current window.

I don't have seprate x screens.

Here is my xorg.conf
> 
Section "Monitor"
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
	Option 		"AllowGLXWithComposite" "true"
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
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
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

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

