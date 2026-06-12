---
title: "915GMA dual head help needed."
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by thirnit on 2007-06-18
what I'm using:

```
Linux lix 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 i686 GNU/Linux

```

UbuntuStudio 7.04

the rig is a dell inspiron B130 with a native lcd of 1280x800.  the graphics adapter is an Intel 915GM. 915resolution is installed and works (i think). i have a dell 1907fp that i am using as an external monitor.  

currently i have output at 1280x1024 to the dell 1907fp (external).  the laptop is displaying 1280x1024 as well however it is simply cloned.  i have the main desktop on both monitors.

my xorg currently says this:

```
Section "Device"
	Identifier	"i915GM"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"B130 15.4WXGA"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"i915GM"
	Monitor		"B130 15.4WXGA"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
```

what has to be done in order to use the external monitor as the main desktop, and the laptop as the extended desktop?

i am a neophyte in most areas linux, so i don't have the full picture (no pun intended) regarding what most xorg components do.  

is there another who has this laptop and has succeeded with dual head? 

your insights are requested!

---

### Post by d-Pixie on 2007-07-16
Hope you haven't given up yet ;o)

Fist off, are you sure the comp. _can_ display two desktops at once? I run a dell inspiron 1300 my self and I sure haven't been able to get it to run different desktops at once.

Most laptops, the cheap ones at least, won't allow this. The external screen connector is more in the line of a comp. to projector connection. Or for use with a better display when available. But sure, it could work and I haven't checked if I can do it under linux ;o)

So, second off, have you checked some related google searches? I know I read a how to on this a while back when fiddeling with beryl or some other. Try checking for "normal" dual screen setups. The spring point being the part where they declare two monitors ;o)

To tell X about several screens on the same card you can do like this (taken from my stationary xorg.conf configured with two cards and three screens):

```

Section "Device"
        Identifier      "ATI0"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "on"
        Option          "RenderAccel"   "true"
        Option          "ForceMonitors" "crt1"
        Busid           "PCI:1:0:0"
        Screen  1
EndSection

Section "Device"
        Identifier      "ATI1"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "on"
        Option          "RenderAccel"   "true"
        Option          "ForceMonitors" "crt1"
        Busid           "PCI:1:0:0"
        Screen  0
EndSection
```

Nm the bloggy code and just compare at a glance. The two devices are the same card and are thus specd the same, bar the last line. The screen tells X that your intrested in one or the other of the two possible screens on the graphics card. Think you can edit the Busid line to read "PCI:1:1:0" or "PCI:1:0:1" on the second device and skip the screen, but I havent tried ;o)

So whats with the devices? Well more code:

```

Section "Monitor"
        Identifier      "Nokia 446pro"
        Option          "DPMS"  "true"
        Horizsync       30-107
        Vertrefresh     50-150
EndSection

Section "Monitor"
        Identifier      "Dell 1704FPT Flat Panel Monitor"
        Option          "DPMS"  "true"
        Horizsync       30-81
        Vertrefresh     56-76
EndSection
```

This then is the two monitors I'd like to use. Modify yours to suite ...

```

Section "Screen"
        Identifier      "Screen CRT"
        Device          "ATI0"
        Monitor         "Nokia 446pro"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024_98.00"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen LCD"
        Device          "ATI1"
        Monitor         "Dell 1704FPT Flat Panel Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024_75.00"
        EndSubSection
EndSection
```

And this is the gold. These two sets up a defined adapter (device) to a specified screen (monitor) to form a working display (screen). X terms in parenthesis ;o)

Try playing with this and search google for more info. If I get round to it I will try to work out if I can run dual on my laptop and write a guide ;o) Good luck!

/d-Pixie

---

### Post by groggyboy on 2007-07-24
i'm also trying to get dual-head working on my 915GMA laptop (i just got my hands on an old monitor!=D> ).

i found the following threads that may be helpful (i don't know if they work, cuz i'm still just experimenting right now):

[http://ubuntuforums.org/showthread.php?t=497136]("http://ubuntuforums.org/showthread.php?t=497136")
[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")
[http://ubuntuforums.org/showthread.php?t=361124]("http://ubuntuforums.org/showthread.php?t=361124")
       ^-----  i used this one to get my s-video working, but i haven't gotten it working for dualhead

i'll post back if i get it working.

---

