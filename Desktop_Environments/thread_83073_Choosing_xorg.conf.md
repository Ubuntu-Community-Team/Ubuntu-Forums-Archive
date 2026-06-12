---
title: "Choosing xorg.conf"
date: 2005-10-27
forum: Desktop Environments
---

### Post by pauljwells on 2005-10-27
Is there a way of automatically selecting a different xorg.conf for different window managers? I have dual monitors and wanted to be able to select between 'BigDesktop' for Gnome and 'Dual Head' for KDE (ie one screen spread over two monitors, or one screen per monitor). The reason is that Gnome crashes on the Dual Head, at least with the ATI drivers.

I was guessing I need to set the machine to boot to a console, rather than the X login screen, then I could have a script to automate the selection??

That said, I don't know how to go about actually *doing* either of those tasks!

Thx in advance

---

### Post by aysiu on 2005-10-29
The only thing I can think of, and this may be a little bit of overkill as a workaround, is dual-booting window managers instead of just having them on the same installation. You could set this up using PartImage (copying an entire partition), then modifying the /etc/X11/xorg.conf file for one installation, leaving it alone for the other.

---

### Post by pauljwells on 2005-10-30
I was wondering if I could have two different 'Server' sections in xorg.conf. How does it work if you want to run a laptop on its own and sometimes with a second monitor for example?

At the moment I just keep two copies of xorg.conf and just sudo cp the right one to /etc/X11 before rebooting and wondered how I could write a script that would do this for me.

---

### Post by ranf on 2005-10-30
[QUOTE=pauljwells]I was wondering if I could have two different 'Server' sections in xorg.conf. How does it work if you want to run a laptop on its own and sometimes with a second monitor for example?[/QUOTE]

According to `man xorg.conf' you can have more than 1 ServerLayout section:
```
SERVERLAYOUT SECTION
       The  config  file  may  have multiple ServerLayout sections.  A "server
       layout" represents the binding of one or more screens (Screen sections)
       and one or more input devices (InputDevice sections) to form a complete
       configuration.  In multi-head configurations,  it  also  specifies  the
       relative  layout  of  the  heads.  A ServerLayout section is considered
       "active" if it is referenced by the -layout command line option  or  by
       an  Option  "DefaultServerLayout" entry in the ServerFlags section (the
       former takes precedence over the latter).  If  those  options  are  not
       used,  the  first ServerLayout section found in the config file is con-
       sidered the active one.  If no ServerLayout sections are  present,  the
       single  active  screen and two active (core) input devices are selected
       as described in the relevant sections above.

```
I haven't tried that yet.

---

### Post by ranf on 2005-10-30
[QUOTE=pauljwells]
I was guessing I need to set the machine to boot to a console, rather than the X login screen, then I could have a script to automate the selection??
[/QUOTE]
Under System -> Systemconfig -> Services simply uncheck gdm. You would then start X with `startx'.

---

### Post by starscalling on 2005-10-30
ive not tried selecting multiple server layouts either... though ive managed to make more than one dual monitor setup work.. ill see what i can do making multiple sections for device/monitor/screen. what i have for my prefered setup is this:

[HTML]Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option          "TwinView"	"on"
	Option          "MetaModes"	"1280x1024,1280x1024; 1024x768,1024x768"
	Option          "SecondMonitorHorizSync"	"30-65"
	Option          "SecondMonitorVertRefresh"	"50-75"
	Option          "TwinViewOrientation"		"RightOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection[/HTML]


this lets me maximize apps on either screen, not across screens [i don't use monitors that are the same size nor directly next to each other so that is not usefull for me], while being able to drag open applications from one screen to the other. ive panels on either screen with window list's so that they show the application open on each monitor independantly :)
for my secondary setup ive come up with this after a bit of reading:

[HTML]
Section "Device"
	Identifier	"fx5200_0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen		0
EndSection

Section "Device"
	Identifier	"fx5200_1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"fx5200_0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "Screen"
	Identifier	"Screen1"
	Device		"fx5200_1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
	Identifier	"Default Layout"
	Screen	0	"Screen0"
	Screen  1	"Screen1" rightof "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
[/HTML]

so im going to try to take that section from the second one i pasted there and define those as monitor2, monitor3 etc and make a section at the bottom calling those.... though it doesnt seem clear from what ive read thus far how i could change between serverlayout sessions.... we shall see :P

[edit adding info so as not to double post :) ]
ok i changed the conf to:

[HTML]Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option          "TwinView"	"on"
	Option          "MetaModes"	"1280x1024,1280x1024; 1024x768,1024x768"
	Option          "SecondMonitorHorizSync"	"30-65"
	Option          "SecondMonitorVertRefresh"	"50-75"
	Option          "TwinViewOrientation"		"RightOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "Device"
	Identifier	"fx5200_0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen		0
EndSection

Section "Device"
	Identifier	"fx5200_1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"fx5200_0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "Screen"
	Identifier	"Screen1"
	Device		"fx5200_1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"Layout1"
	Screen	0	"Screen0"
	Screen  1	"Screen1" rightof "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection[/HTML]

which let me define more than one serverlayout section... and i asked the #xorg guys what to do to select the second serverlayout. they said use the X -layout layoutnamehere option.. which doesnt exactly work... it starts X but not the GDM and i can't use that option from sudo /etc/X11/gdm [start/stop/etcetcetcetc] so if someone cracks this that would be fun :P

---

### Post by ranf on 2005-10-31
[QUOTE=starscalling]which let me define more than one serverlayout section... and i asked the #xorg guys what to do to select the second serverlayout. they said use the X -layout layoutnamehere option.. which doesnt exactly work... it starts X but not the GDM and i can't use that option from sudo /etc/X11/gdm [start/stop/etcetcetcetc] so if someone cracks this that would be fun :P[/QUOTE]
I found this in the GDM help file where it discusses the /etc/gdm/gdm.conf:

StandardXServer

StandardXServer=/usr/X11R6/bin/X

    Full path _and arguments_ to the standard X server command. This is used when gdm cannot find any other definition, and it's used as the default and failsafe fallback in a number of places. This should be able to run some sort of X server.

---

### Post by starscalling on 2006-01-24
heh i think i should take up that project again :D
i was thinking perhaps one could define sessions like that..
have two gnome/kde/openbox etc sessions :D

---

