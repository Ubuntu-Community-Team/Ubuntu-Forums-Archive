---
title: "Dual Monitor on Intel 915GM - Primary Head?"
date: 2007-04-25
forum: Desktop Environments
---

### Post by mynnx on 2007-04-25
Greetings!  I posted a few days ago trying to figure out how to get a picture on my other monitor connected to the VGA port of my HP dv4170us laptop.  Well, I've now figured that out, but I'm having problems with X knowing which monitor is which.   To be honest, I don't see anywhere in the xorg.conf file where a distinction is made, and it keeps loading my panels and stuff in the external monitor instead of my laptop's flat panel.

In addition, I need to use 915resolution to get the 1440x900 my external monitor supports.  I know how to run it (/etc/init.d/915resolution start after modifying the file), but how do I automate this process at the correct time in the X launch sequence?

Here are my xorg.conf and my Xorg.0.log files for my current setup.  Any help would be greatly appreciated!

```

*...font, inputdevice stuff....*
Section "Device"
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	64.7
	VertRefresh	60.0
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1400x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" LeftOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```

```

http://paste.ubuntu-nl.org/17715/http://paste.ubuntu-nl.org/17715/

```

Thanks!

---

### Post by Aetherius on 2007-04-26
Go into the display section of your BIOS configuration, there is an option for which screen to use at boot

;)

---

### Post by rignes on 2008-03-12
Did you ultimately get this to work?  If so, can you say what you did?  I'm in the same boat as you.

Thanks.

---

