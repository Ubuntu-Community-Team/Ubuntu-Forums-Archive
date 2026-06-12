---
title: "Mouse sensitivity WAY up, double clicking at random"
date: 2009-03-10
forum: General Help
---

### Post by snowveil on 2009-03-10
Hello all,

Recently Ubuntu failed to shut down all of the way so I unfortunately had to restart it using the reset switch, and upon restarting my mouse started acting very strangely.  The mouse sensitivity seems to have doubled, and every time I click (left or right) Ubuntu recognizes it as a double-click.  I looked in my xorg.conf file and there didn't appear to be anything off in the "mouse" section to the best of my knowledge.

I am for some reason unable to load up the "Mouse" program under the system/preferences menu...I get a tab that says "Starting Mouse..." that just closes soon after with no window coming up.

I tried out two different mice, both were having the same problem.  I tried restarting X, same issue.  I tried restarting the machine entirely, and it locked up upon shutting down again.

Any ideas?

---

### Post by snowveil on 2009-03-11
update:

I've noticed that if I restart X, the mouse sensitivity is just fine before loading the Gnome login screen (when the cursor is just an "X")...but as soon as the login screen loads up it starts going haywire with the sensitivity.

Every mouse action I perform (movement and clicking) appears to be doubled....it makes the system almost unusable.  

Is it possible that the mouse configuration is somehow doubled?  Being loaded from two places?

---

### Post by snowveil on 2009-03-11
bump and another update...

I ran xev through a terminal window and it appears as though every event is yielding a TRIPLE event, not just a double event.  Any event (mouse move, right/left/scroll click) is listing 3 times with the xev output as having the same TIME parameter.

can anyone throw me a bone here?  I've been searching google all morning to no avail.

---

### Post by snowveil on 2009-03-11
bump again....

tried a third mouse, same problem.  Here's a copy of my xorg.conf file in case it is of any help :-/

```


Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1905FP (Digital)"
	Horizsync	30.0	-	81.0
	Vertrefresh	56.0	-	76.0
	Gamma	1
	modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline  "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline  "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	modeline  "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"RandRRotation"	"true"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	DefaultDepth	24
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Option 		"Device" "/dev/input/mice"
	Driver		"mouse"
	Option		"Buttons" "5"
	Option		"ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "stylus"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "eraser"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "cursor"
	Option        "Mode"          "relative"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
#	Inputdevice	"Configured Mouse"	"CorePointer"
	InputDevice    "stylus"    "SendCoreEvents"
	InputDevice    "eraser"    "SendCoreEvents"
	InputDevice    "cursor"    "SendCoreEvents"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
	Option		"NoLogo"	"True"
	Option "RandRRotation" "true"
	Option "Rotate" "left"
	Driver	"nvidia"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Option		"UseDisplayDevice" "CRT,DFP"
	Option "RandRRotation" "true"
	Screen	1
	Driver	"nvidia"
EndSection

```


The wacom tablet I'm using works just fine.  On an unrelated note...My xorg.conf feels very cluttered...does anyone see some redundancies that I could remove?

---

### Post by Favux on 2009-03-11
Hi snowveil,

What version of Ubuntu are you using?  Need to know that before working on xorg.conf.  Also do you know why it says "Boardname	"vesa" " when you seem to have an Nvidia card (at least you're using an Nvidia driver}.

Have you tried fsck?  If you are unfamiliar with it, before use type "man fsck" in a terminal and read carefully.

---

### Post by snowveil on 2009-03-12
Favux, I'm running Ubuntu 8.10 Intrepid Ibex.  In regards to the "vesa" mode, I'm honestly not sure.  I am running an nvidia 6800xt, and I believe that is what was auto-configured through nvidia-settings.  I'm not very well versed with the xorg config file, so I don't poke around in it too much...but I wouldn't mind getting a better grasp of how it works.

---

### Post by Favux on 2009-03-12
Hi snowveil,

What kind of pc are you on?  Do you have a Wacom tablet?  Or do you have a tablet pc?  Which model?  If you don't (have a Wacom tablet) are you planning on getting one?

Did you try to remove the comment from in front of:
```
#	Inputdevice	"Configured Mouse"	"CorePointer"
```
in the "ServerLayout"?

You can ignore that though because in Intrepid HAL (hardware abstraction layer) will run your keyboard and mouse through its .fdi files.  So lets pretend they got commented out like they would have with an upgrade.  Hopefully letting HAL run things will fix the mouse problem.  I also rearranged your sections.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Option 		"Device" "/dev/input/mice"
#	Driver		"mouse"
#	Option		"Buttons" "5"
#	Option		"ZAxisMapping" "4 5"
#EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "stylus"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "stylus"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "eraser"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "eraser"
EndSection

Section "InputDevice"
	Driver        "wacom"
	Identifier    "cursor"
	Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
	Option        "Type"          "cursor"
	Option        "Mode"          "relative"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
	Option		"NoLogo"	"True"
	Option "RandRRotation" "true"
	Option "Rotate" "left"
	Driver	"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1905FP (Digital)"
	Horizsync	30.0	-	81.0
	Vertrefresh	56.0	-	76.0
	Gamma	1
	modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline  "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	modeline  "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	modeline  "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"RandRRotation"	"true"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Option		"UseDisplayDevice" "CRT,DFP"
	Option "RandRRotation" "true"
	Screen	1
	Driver	"nvidia"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	DefaultDepth	24
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Default Screen" 0 0
# commented out by update-manager, HAL is now used
#	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
#	Inputdevice	"Configured Mouse"	"CorePointer"
	InputDevice    "stylus"    "SendCoreEvents"
	InputDevice    "eraser"    "SendCoreEvents"
	InputDevice    "cursor"    "SendCoreEvents"
EndSection
```
Be sure to back up your xorg.conf.  Then compare the two to see what I did.  Hopefully this is a good first pass and will fix the mouse sensitivity problem.

---

### Post by snowveil on 2009-03-12
thanks for the reply, I'll try it out now.

I did just notice something strange.  When I disconnect my wireless keyboard/mouse combo, everything works fine with my other wirless and wired mice.  This keyboard/mouse combo (microsoft) used to be symlinked to /dev/js0, but for some reason /dev/js0 is no longer available.  As soon as I hook the keyboard and mouse back up, I'm back to where I started.

---

### Post by Favux on 2009-03-12
Hi snowveil,

Do you know where the symlink was?  Was in in /etc/udev/rules.d or was it in the HAL version?  When did you upgrade to Intrepid?  Or was Intrepid the first Ubuntu you installed?

---

### Post by snowveil on 2009-03-12
I started with 8.04LTS and upgraded to Ibex the week it was released.

Honestly, I'm not sure how the link was created.  Rebooting and running jscalibrator caused the microsoft mouse/keyboard to be recognized under js0 and js1 again...

```

$ ls -li /dev/input/by-id/usb-Microsft_Microsoft_Wireless_Desktop_Receiver_3.1-event-kbd 
12835 lrwxrwxrwx 1 root root 9 2009-03-12 20:35 /dev/input/by-id/usb-Microsft_Microsoft_Wireless_Desktop_Receiver_3.1-event-kbd -> ../event5

```

for some reason the link appears to be sent to /dev/input/event5 whereas jscalibrator recognizes the keyboard/mouse receiver as /dev/input/js0 and /dev/input/js1

could this be part of the issue?  I'm not sure if it was symlinked to /dev/input/event5 before

---

### Post by Favux on 2009-03-12
Ok, if the symlink was created in Hardy and survived upgrade to Intrepid it's probably in rules.d somewhere.

Do you mind terribly answering my questions above?  Did the edited xorg.conf do anything?

Could you describe your bluetooth setup.  Built in or a dongle.  Multiple keyboards and mouses on it?

---

### Post by snowveil on 2009-03-12
Sorry I wasn't clear enough before :)

The keyboard I'm running isn't actually bluetooth, it is a standard RF receiver for a wireless microsoft Keyboard and mouse bundle (Microsoft Laser 6000 if I'm not mistaken).  I don't care much for the microsoft mouse, so I'm currently also running a logitech mx700 wireless mouse.

The edited xorg.conf did not appear to make any changes.

I do have a wacom tablet, and it appears to be working just fine.

This problem seemed to just randomly happen.  I shut down my system to install a new hard drive to back up files....backed them up...then shut down, removed the drive, and upon booting up again it started happening.  I'm not sure if it's a result of that or if some updates did not finish installing until I rebooted, because I don't recall doing much in X outside of the copying of files through the terminal window.

I don't know much about what you mean with rules.d.  I can see the list of files, but there don't appear to be any specific symlinks located in them.

---

### Post by Favux on 2009-03-12
Hi snowveil,

With keyboard and mouse commented out you're closer to having an Intrepid style xorg.conf.  Originally your xorg.conf was Hardy style, except maybe for the mouse commented out in "ServerLayout".  You could now remove those entries or leave them commented out.  But be sure to save labeled copies of them somewhere if you remove them.

In /etc/udev/rules.d the bluetooth stuff would be in something like 62-bluez-hid2hci.rules and the symlinks could be in 60-symlinks.rules.  Unfortunately they could be other places.  Given that it's not reproducible you have a tough problem.

---

