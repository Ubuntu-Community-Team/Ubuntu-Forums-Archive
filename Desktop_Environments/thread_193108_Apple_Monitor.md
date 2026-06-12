---
title: "Apple Monitor"
date: 2006-06-09
forum: Desktop Environments
---

### Post by dareofficer on 2006-06-09
I have a apple 20 in dvi monitor.  I see it in settings just fine.  I only can get 1024 rez, at 60 hrz.  It should be able to do 1600.  How do I change this??  I have been suse 10.1, and it took right off.  I'm new to Linux, so any help would be great.  

Thanks!:D

---

### Post by patrickfromspain on 2006-06-09
You should maybe edit your settings in /etc/X11/xorg.conf.

sudo gedit /etc/X11/xorg.conf

there look for something similar to this:

SubSection "Display"
		Depth		24
		Modes		"1280x1024_60" "1024x768" "800x600" "640x480"
EndSubSection

and add your resolution, so it ends up being:
Modes		"1600x1200_60" "1280x1024_60" "1024x768" "800x600" "640x480"

Then, reboot and it should be fine. If you get a command line interface:

sudo nano /etc/X11/xorg.conf, delete "1600x1200_60", control+O to save and control+x to exit. then reboot.

EDIT: apple 20" dvi monitor.. lucky you ;)

---

### Post by dareofficer on 2006-06-09
There is nothing in xorg.conf?  Do I need to create that file?  I'm very new to linux.

---

### Post by Ramses de Norre on 2006-06-09
There must be a xorg.conf, you can't run any graphical program without it. Be sure to copy the path correctely.

---

### Post by dareofficer on 2006-06-09
Thanks, you were right.  However it is still not working.  Does this mean my display driver is not working right?

Thanks for the help!



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
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
                             Depth 24
Modes "1280x1024_60" "1024x768" "800x600" "640x480"
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

---

