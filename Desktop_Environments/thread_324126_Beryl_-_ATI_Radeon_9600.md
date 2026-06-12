---
title: "Beryl - ATI Radeon 9600"
date: 2006-12-23
forum: Desktop Environments
---

### Post by Wahlqvist on 2006-12-23
I get this when i try to start "beryl-manager" 

"wahl@wahl-desktop:~$ beryl-manager
wahl@wahl-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension"

and **YES** i have installed the ati radeon driver and everything (this guide[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") )
and my device setting is : 

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "radeon"
	Option	    "AGPFastWrite" "yes"
	Option	    "AGPMode" "4"
	Option	    "ColorTiling" "on"
	Option	    "EnablePageFlip" "true"
	Option	    "AccelMethod" "EXA"
	Option	    "XAANoOffScreenPixMaps"
	Option	    "RenderAccel" "true"
	Option	    "DRI" "true"
	BusID       "PCI:1:0:0"
EndSection

so now i ask, is there any1 that can tell me how to fix beryl on my ATI ( i know my drivers work cuz' before i "installed them" i couldn't play q3, and now after the "install" i can )

_Please help me_ 
and thanks

---

### Post by kalikiana on 2006-12-23
I recommend to visit #ubuntu-xgl on chat.freenode.net for a question like this.

---

### Post by Stemp on 2006-12-23
«beryl: No composite extension»

Just add this section to your xorg.conf :

Section "Extensions"
 Option "Composite" "Enable"
EndSection

---

### Post by Wahlqvist on 2006-12-23
well my cpu crashes when i try to start it now, how to fix that then? it just freezes when i write "beryl" or "beryl-manager" 

some other thing i must change?

---

### Post by Stemp on 2006-12-23
Here is my xorg.conf (work with beryl on an ati 9600) :

[xorg.conf]("http://ubuntufr.free.fr/upload/xorg.conf.dec2006")

---

### Post by Wahlqvist on 2006-12-23
okiii ty man, hope it works

---

### Post by Wahlqvist on 2006-12-23
how to get back ,y 1600/1200 , and ,y old keybord

---

### Post by Stemp on 2006-12-23
Look in your former xorg.conf (if you don't save it, it's probably /etc/X11/xorg.conf~ )

The Keyboard :
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

The screen resolution :
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI 9600"
	Monitor		"NEC CI LC700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	Option 			"AddARGBGLXVisuals" "true"
EndSection
```

or juste change the Modes to Modes "1600x1200" "1024x768"

---

### Post by jenigmat429 on 2006-12-24
I've tried to install Beryl with an Intel Corporation Mobile 945GM/GMS/940GML video card also on Edgy and am getting the same message. I've tried to add those three lines to my xorg.conf, but it still gives me the same message.

---

