---
title: "Dell D620 and Dell external monitor problems"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by croman22 on 2008-02-06
Hi, 

I am having a problem getting a D620 laptop and a new Dell 1908WFP 1440x900 monitor to work.  The laptop screen is 1440x900, and works fine.  

When I plug in the external monitor and hit Fn-F8 the monitor complains the signal is out of range and to please use a 1440x900 60Hz signal.  If I hit Fn-F8 again a picture shows up on the monitor.  It is fuzzy and unclear.  If I use the monitor buttons to check what signal it thinks it is getting it may say 1152x900 at 60Hz or 1440x900 at 62 Hz.  If I hit Fn-F8 a few more times both screens go black never to return.  I've tried messing with my xorg.conf to set it up for two screens.  No matter what the external shows up with the resolution is wrong.

What I want is the external monitor to be a copy of my laptop screen.


Here are some basic facts:
  
>>>>sudo lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

I'm current on all available packages.

>>>>lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

driver: 810i

is have 915resolution installed and "/usr/sbin/915resolution 45 1280 800" in my rc.local

Excerpt from a xorg.conf that I tried to get a dual display going with no luck is here....... The dual head is not what I want but I tried it anyway.  I'm no xorg.conf ninja and admit to not understanding the details of "clone" and "Xinerama" and where they can be used. 

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller
"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 0
        Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 1
        Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Laptop Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller
"
        Monitor         "Laptop Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "Device1"
        Monitor         "External"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Dual Monitor Layout"
        Screen 0 "Laptop Screen" 0 0
        Screen 1 "Secondary Screen" LeftOf "Laptop Screen"
        #Option "Clone" "On"
        Option "Xinerama" "On"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by croman22 on 2008-02-08
Solved my own problem.  Here are the pieces from two working xorg.conf's.  the trick was getting the mode line in there. otherwise 
the monitor will be driven at every resolution other than the correct one. 

Dual Screen:

###############

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 0
	Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier	"Device1"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 1
	#Option "Clone" "true" 	
	Option "MonitorLayout" "CRT,LFP"
EndSection

###############

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"External"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
        Modeline "1440x900@60" 106.5 1440 1520 1672 1904 900 903 909 934
EndSection

################

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Laptop Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"Device1"
	Monitor		"External"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1440x900@60"
	EndSubSection
EndSection

################

Section "ServerLayout"
	Identifier	"Dual Monitor Layout"

	Screen 0 "Laptop Screen" 0 0	
	Screen 1 "Secondary Screen" above "Laptop Screen" 
	Option "Xinerama" "On"
	
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection






 And this is for Clone: 
#############

Section "Device"
	Identifier	"Intel IGC"
	Driver		"i810"
	BusID		"PCI:0:2:0"	
	Screen 0 
	Option "MonitorLayout" "CRT,LFP" 
EndSection

Section "Device"
	Identifier	"Intel IGC Clone"
	Driver		"i810"
	BusID		"PCI:0:2:0"	
	Option "MonitorLayout" "CRT,LFP" 
	Option "Clone" "on"
	Screen 0 
EndSection

#############

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"External"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
        Modeline        "1440x900@60" 106.5 1440 1520 1672 1904 900 903 909 934
EndSection

#############

Section "Screen"
	Identifier	"LFP Screen"
	Device		"Intel IGC"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Intel IGC Clone Screen"
	Device "Intel IGC Clone"
	Monitor "External"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1440x900@60"
	EndSubSection
EndSection

#############

Section "ServerLayout"
	Identifier	"Clone Layout"
	Screen		"Intel IGC Clone Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

