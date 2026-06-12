---
title: "Problem with Xinerama"
date: 2006-11-20
forum: Desktop Environments
---

### Post by ordel65 on 2006-11-20
Hi,

I've got a problem with my Xinerama config. I have two screens, a LCD one (1280x1024) and a CRT one (1024x768) on a single ATI X300SE, and i'd like to have an extended desktop.
The main screen is the LCD one and is on the vga port, and the CRT one is on the DVI port (with an adaptor).
The CRT one is at the left of the other.
My problem is that both screens show the left part of my desktop.

This is my xorg.conf :

> 
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

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
	Identifier	"0 ATI_Radeon_X300"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MonitorLayout" "TMDS, CRT"
	Screen	0
EndSection

Section "Device"
	Identifier	"1 ATI_Radeon_X300"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MonitorLayout" "TMDS, CRT"
#	Option          "TVOutFormat" "Composite" #or SVIDEO etc 
#   	Option          "TVStandard" "PAL-G" #or NTSC, PAL-I for uk etc 
#   	Option          "ConnectedMonitor" "TV"
	Screen	1
EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
#	HorizSync	31-80
#	VertRefresh	56-75
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#	HorizSync	31-80
#	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI_Radeon_X300"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI_Radeon_X300"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Main Screen"
	Screen 1	"Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

# Section "DRI"
# 	Mode	0666
# EndSection


Can you help me....

Thanks

---

### Post by wieman01 on 2006-11-20
There is a sample configuration for my laptop using Xinerama with an external device. You basically have to duplicate "Device", "Monitor", and "Screen" which you have not done yet. Your setup is a bit different though so you may have to adjust the "BusID" of the second device:
> PCI:0:2:0
This is my "xorg.conf":
[HTML]Section "Device"
	Identifier	"Internal Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"	"CRT,LFP"
	Screen 		0
EndSection

Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite" 
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	HorizSync	30-60
	VertRefresh	50-75
	Option		"DPMS"
	Modeline    	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection	
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Head"
	Screen		"Internal Screen"
	Screen		"External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection[/HTML]

**_EDIT:_**
Check out this HOWTO: [http://www.ubuntuforums.org/showthread.php?p=1773624]("http://www.ubuntuforums.org/showthread.php?p=1773624")

---

### Post by alphapogo on 2006-11-21
Hi there,

maybe I found two errors in your xorg.conf (at least it wouldn't work on my box)

in 
Section "ServerFlags"
         Option "Xinerama" (remove "true")
EndSection 

while in

Section "ServerLayout"
         Option "Xinerama" "true" 
...
is missing

then in both 

Section "Device"
         Option "MergeFB" "true"
....
is missing (I think this is an ATI thing, without this Option I get only "Cloned Dual Head" Mode. IMHO this might be the cause of your prob.

and (also in both Section "Device" I'd use 
           Option "MonitorLayout" "CRT" 
only. 
Not sure about that, but maybe I have probs with "TMDS" and "LCD" because my LCDs are a litte old *g*. Just try it out...

Hope this helps.
Greetings
alphapogo

---

