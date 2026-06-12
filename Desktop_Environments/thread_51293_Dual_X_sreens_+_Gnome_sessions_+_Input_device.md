---
title: "Dual X sreens + Gnome sessions + Input device"
date: 2005-07-23
forum: Desktop Environments
---

### Post by unzari on 2005-07-23
I have set up dual X screens on my Nvidia card... not TwinView.  (I tried that too, but I prefer having separate X screens... no confusion over resolutions between them, and you can explicitly start applications on the display you want.)

One of these is just my normal monitor, while the other is my flat panel display for watching movies.

My questions are:

**1)**  A gnome sessions starts on the flat panel.  That's not such a problem, but it seems like a waste of memory.  Since I'll work on the normal monitor, I'd like to know *how to tell gnome not to start that second session*.  And, in line with this of course...

**2)** This session has no input device (keyboard, mouse).  *How would I set one up*?  In fact, I'd like to set 'lirc' up to control that session if I don't disable it.


Interestingly, the 'xorg.conf' file is one I set up on a FC4 installation (on the same machine) and ditched for Ubuntu. However, there was no gnome session on the FC4 installation (which I think is more likely a bug on FC4)!

For anybody who may wish to set up a similar thing, I'm including my 'xorg.conf*' files below, one for my 'DualScreens' setup and one for the 'TwinView setup.  The info came straight from a couple of very good articles on the Nvidia site.  If you replace your own 'xorg.conf' files with one of these, make sure you set the correct PCI address in the 'Device' sections!  (Use 'lspci'.)

################################################
# START
################################################
# Separate X displays (:0.0 and :0.1)

Section "ServerLayout"
	Identifier     "NVIDIA DualScreen layout"
	Screen      0  "LCD" 0 0
	Screen      1  "DFP" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	FontPath     "unix/:7100"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	#Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "LCD"
	VendorName   "Sony"
	ModelName    "Sony SDM-HS93"
	DisplaySize  380	300
	HorizSync    28.0 - 65.0
	VertRefresh  48.0 - 65.0
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "DFP"
	VendorName   "Hitachi"
	ModelName    "Digital Flat Panel PW1"
	HorizSync    31.5 - 57.0
	VertRefresh  50.0 - 70.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "nvidia0"
	Driver "nvidia"
	BusID  "PCI:1:0:0"
	Screen 0
        Option      "DigitalVibrance" "128"
EndSection

Section "Device"
	Identifier  "nvidia1"
	Driver "nvidia"
	BusId  "PCI:1:0:0"
	Screen 1
        Option      "DigitalVibrance" "96"
        Option      "FlatPanelProperties" "Scaling=native, Dithering=default"
                        # Scaling = default | native | scaled | centered | aspect-scaled
                        # Dithering = default | enabled | disabled
EndSection

Section "Screen"
	Identifier  "LCD"
	Device "nvidia0"
	Monitor "LCD"
	DefaultDepth 24
	Subsection "Display"
	    Depth  24
	    Modes  "1280x1024" "1024x768" "800x600" "640x480"
	EndSubsection
EndSection

Section "Screen"
	Identifier  "DFP"
	Device "nvidia1"
	Monitor "DFP"
	DefaultDepth 24
	Subsection "Display"
	    Depth  24
	    Modes  "1024x768" "800x600" "640x480"
	EndSubsection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

################################################
# END
################################################

################################################
# START
################################################
# Setup for Nvidia TwinView dual displays

Section "ServerLayout"
	Identifier     "NVIDIA TwinView layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"

# RgbPath is the location of the RGB database.  Note, this is the name of the 
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)
# By default, Red Hat 6.0 and later now use a font server independent of
# the X server to render fonts.
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	FontPath     "unix/:7100"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	#Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Sony SDM-HS93"
	DisplaySize  380	300
	HorizSync    28.0 - 65.0
	VertRefresh  48.0 - 65.0
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor 1024x768"
	HorizSync    31.5 - 57.0
	VertRefresh  50.0 - 70.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "Realtek WinFast"
	BoardName   "NVIDIA GeForce FX 5500"
	Option	    "TwinView"
	Option      "ConnectedMonitor" "CRT, DFP"	# CRT, DFP, TV
	#Option	    "MetaModes" "1280x1024,1024x768; 1152x864,1024x768; 1024x768,1024x768; 1024x768,NULL; NULL,1024x768"
	Option	    "MetaModes" "1280x1024,NULL; 1024x768,1024x768"
	Option	    "SecondMonitorHorizSync" "31.5 - 57.0"
	Option	    "SecondMonitorVertRefresh" "50.0 - 70.0"
	#Option	    "TwinViewOrientation" "Monitor0 LeftOf Monitor1"
	Option	    "TwinViewOrientation" "Clone"
	Option      "DigitalVibrance" "32"
	Option      "FlatPanelProperties" "Scaling=centered, Dithering=default"
			# Scaling = default | native | scaled | centered | aspect-scaled 
			# Dithering = default | enabled | disabled
	                                                                      
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     16
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "1280x1024" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection
################################################
# END
################################################

---

### Post by unzari on 2005-07-26
Nobody has any idea?  ](*,)

---

### Post by jlapier on 2007-03-01
I realize this is a pretty old post, but I'm just here to say thanks for posting your xorg.conf files. I wanted to get dual x-sessions going on my two monitors, both with different resolutions. Twinview works great for using two screens with different resolutions in Gnome, of course, but I use wmii as my window manager most of the time on this particular machine, and multiple X displays was the way to go for me.

Thanks again!

- Jason

---

### Post by op157 on 2007-03-24
I may have this problem.  I want to get the same screen two appear on two displays with different resolutions (with the lower resolution one showing a scaled version of the higher resolution one).  I posted it here:

[http://ubuntuforums.org/showthread.php?p=2346280#post2346280]("http://ubuntuforums.org/showthread.php?p=2346280#post2346280")

Will this 2nd xorg.con file solve it?  Sorry I can't try it out right now, but I don't have access to the computer until sunday ~ midnight.

---

