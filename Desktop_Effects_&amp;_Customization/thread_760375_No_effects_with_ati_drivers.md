---
title: "No effects with ati drivers"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by meimato on 2008-04-20
I just upgraded from Gutsy to Hardy RC1.
In Gutsy I was using ati drivers (the open drivers), becouse fgrlx drivers have always made my system unstable: I've got a Mobility Radeon 9600, which is supported, but I've never been able to use hardware acceleration properly.
By the way: even using the ati drivers, I was able to have compiz running; now, after the upgrade to Hardy, I cannot use desktop effects: if I try to enable them, an error message appears stating that it is impossible to enable them.

fglrx drivers from Hardy repository have the same effect on my system: they make it randomly crashing; I tried to use Envy, but it crashed during the configuration (the error is in the attached file).


I doesn't necessarily want to have the accelerated drivers running; it would be sufficient to me to enable desktop effects with ati (or radeon) drivers.

---

### Post by robertchahine on 2008-04-20
i had a problem like this with the ati drivers, but when i installed this it worked really great:
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl

```

---

### Post by meimato on 2008-04-20
Yes, if I install fglrx drivers desktop effects work; the problem is that my system becomes unstable: that's why I'd like to enable effects using ati drivers, like I've always do with past versions of Ubuntu.

---

### Post by Zorael on 2008-04-20
It should work (albeit performance will be dismal) if you install the xserver-xgl package. You'll need to restart your X server, of course. Ctrl+Alt+Backspace.

Make sure you have it, then post the output of the following command entered in a terminal.
```
$ compiz --replace &
```

---

### Post by meimato on 2008-04-20
Ok, I installed xserver-xgl and enabled fglrx drivers: up now, the system didn't crash; desktop effects works, but I think there's still something wrong: it seems I haven't full acceleration.

This is the result if I run fglrxinfo

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)


This is the output of compiz --enable &

luckyland@UbuntuA2810:~$ Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/show_desktop_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/show_desktop_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_all_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_group_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/expo/allscreens/options/expo_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


glxgears reports about 110 fps.


Finally I've got a strange behavior of gdm with fglrx enabled: my gdm welcome screen appers not centered in the screen, but rather set up at a higher resolution than the one I have; I've got a native resolution of 1400x1050, which works well with my desktop session: in the gdm welcome screen I can only see the user entry field in the lower right corner of the scree.



Enough? :-)
Thanks

---

### Post by Zorael on 2008-04-20
I'm not sure I can help you with the fglrx drivers. That is what you want to work on though, I'd say; getting fglrx to work with your system while keeping it stable. I'd try [Envy](http://albertomilone.com/nvidia_scripts1.html) and see if the driver version it installs works better with your card.

xgl performance *will* be dismal.


If you enable fglrx, we'd like to see your /etc/X11/xorg.conf file to see if there are any anomalies with the resolutions defined there. As for the stability issues, see if Envy does the trick.

---

### Post by meimato on 2008-04-20
Thank you.
I tried Envy, but it exits with the errors you can see in the attached image to my first post.

My xorg.conf is the following:

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"stylus"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"eraser"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"cursor"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen		0
	Option		"MergedFB"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"LCD Panel"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"LCD Panel"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1400x1050@60"	"1400x1050@75"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #                                               
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen		1
	Option		"MergedFB"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection
Section "screen" #                                               
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	
	EndSubSection
EndSection
Section "monitor" #                                               
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by Zorael on 2008-04-20
True, you did mention Envy; memory failed me.

Your xorg.conf is needlessly messy. Make a backup and create a new one with the following content.
```
Section "ServerLayout"
	Identifier "Default Layout"
	Screen 0 "Default Screen" 0 0
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "it"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizEdgeScroll" "0"
	Option "SHMConfig" "on"
EndSection

Section "Monitor"
	Identifier "LCD Panel"
	Vendorname "Plug 'n' Play"
	Modelname "Plug 'n' Play"
EndSection

#Section "Monitor"
#	Identifier "monitor1"
#	Vendorname "Plug 'n' Play"
#	Modelname "Plug 'n' Play"
#EndSection

Section "Device"
	Identifier "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Boardname "ati"
	Busid "PCI:1:0:0"
	Driver "fglrx"
	Screen 0
	Option "MergedFB" "off"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

#Section "Device"
#	Identifier "device1"
#	Boardname "ati"
#	Busid "PCI:1:0:0"
#	Driver "fglrx"
#	Screen 1
#	Option "MergedFB" "off"
#	Option "VideoOverlay" "on"
#	Option "OpenGLOverlay" "off"
#EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor "LCD Panel"
	Defaultdepth 24
	SubSection "Display"
		Depth 24
		Modes "1400x1050@60" "1400x1050@75" "1280x960@75" "1280x1024@60" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
	EndSubSection
EndSection

#Section "Screen"
#	Identifier "screen1"
#	Device "device1"
#	Defaultdepth 24
#	Monitor "monitor1"
#	SubSection "Display"
#		Depth 24
#		Modes "640x480@60" "640x480@72" "640x480@75" "800x600@56" "800x600@72" "800x600@75" "800x600@60" "832x624@75" "1024x768@75" "1024x768@70" "1024x768@60" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75"
#	EndSubSection
#EndSection

Section "Module"
	Load "glx"
	Load "GLcore"
	Load "v4l"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```
There were evidence of you having had (at one point?) two monitors connected. The references to the monitors were incomplete, however, so I took the liberty of commenting them. If you still have both connected, remove the commenting hashmarks (#).

At least I believe I found what made things not centered on your screen.

---

### Post by Saint Angeles on 2008-04-20
heres my solution in a different thread:

first remove xserver-xgl as the latest fglrx doesnt need it.

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

enjoy!

---

### Post by Zorael on 2008-04-20
> **Saint Angeles said:**
> heres my solution in a different thread:

first remove xserver-xgl as the latest fglrx doesnt need it.

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

enjoy!
Yes, forgot to mention, as soon as you're dealing with fglrx you want to get rid of xserver-xgl. And the thread linked to seems like just what you're looking for.

---

