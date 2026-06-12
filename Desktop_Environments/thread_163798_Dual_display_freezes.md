---
title: "Dual display freezes"
date: 2006-04-21
forum: Desktop Environments
---

### Post by capitalistpiglet on 2006-04-21
I managed to set up a dual display using a geforce4 mx agp and a geforce2 mx pci card. The problem is every 30 minutes or so the system freezes and the only way to recover is to restart the machine.
this is my xorg.conf file> Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"ctrl:nocaps"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:0:11:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce4]"
	Driver		"nvidia"
	BusID		"PCI:01:00:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"monitor right"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"screen right"
	Device		"NVIDIA Corporation NV11 [GeForce4]"
	Monitor		"monitor right"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen right"
	Screen		"Default Screen" LeftOf "screen right"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "DefaultServerLayout" "Default Layout"
EndSection


Section "DRI"
	Mode	0666
EndSection


---

### Post by OrganicPanda on 2006-04-21
well i certainly cant help

Edit:: ignore me

---

### Post by Jason_25 on 2006-04-21
Is it really locking up?  Can you ctrl-alt-f1 to a virtual terminal?  Can you SSH into it?  

Do you have an AMD cpu with powernowd installed?

Is the video card getting too hot?



Also, examine your logs to see if anything showed up around the time of the lockup.

As for your xorg file, I noticed you were using xinerama.  Have you tried using twinview?  If you want to continue with, xinerama, I would comment out the "UseFBDev" option, and comment out DPMS for now too.  Last resort would be commenting out DRI.

---

### Post by capitalistpiglet on 2006-04-21
thanks for replying, yes it completely locks up, i cannot reach a virtual terminal or restart x using ctrl alt and backspace.
yes i do use have a amd with powernowd is that the problem?
 I tried commenting out dpms and usefbdev but that failed to slve the problem.
As for twinview is that not for dual head cards only?

---

### Post by Jason_25 on 2006-04-21
Yes twinview is for the single cards.  I just skim over posts.

They may have made powernowd into the ubuntu-desktop metapackage so I will show you how to remove it without borking your dist-upgrade path.

```

sudo update-rc.d -f powernowd remove

```

Once you reboot, it should no longer try to clock the cpu down.

---

### Post by capitalistpiglet on 2006-04-22
its still freezing up any other ideas, thanks.

---

### Post by capitalistpiglet on 2006-04-22
also here is the xorg log.

edit---
i solved the problem by swapping the nvidia driver to the nv driver for the geforce2 card. But thanks for your help Jason_25 .

---

