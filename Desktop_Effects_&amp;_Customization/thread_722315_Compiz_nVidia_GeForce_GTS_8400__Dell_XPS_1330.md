---
title: "Compiz nVidia GeForce GTS 8400  Dell XPS 1330"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by herger on 2008-03-12
[SIZE="3"]Hi all.
I have a lot of problems in enabling desktop effects.
Everything started when I tried to install a virtual machine on virtual box.
I lost everthing concerned with the video card and I have been working for a while to re-establish the thing.
I installed the latest nVidia drivers and I have the video card well working now.
When I run  Preferences -> Aspect -> Visual Effects  it "thinks" about it for a while and then says "Desktop effects could not be enabled", without specifying any receipt...
I have read  ALL the posts in the internet regarding xserver-xgl, but if I install it (both from shell and with synaptic) I can't have the x-session working!!!!!!!!!
Do You have any suggestion?

Thanks in advance and the best regards

Herger[/SIZE]

---

### Post by Zorael on 2008-03-12
To my knowledge, you don't want to install xserver-xgl when you have an Nvidia card. Just the nvidia-glx or nvidia-glx-new packages.

Could you post the contents of your /etc/X11/xorg.conf? Also, the output of the following commands in a shell console.
```
$ glxinfo | grep -i rendering
```
```
$ compiz --replace
```

---

### Post by herger on 2008-03-12
Hi!
Thanks for Your reply.
Here are the responsens

$ glxinfo | grep -i rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

Thanks and regards

H

---

### Post by herger on 2008-03-12
Then, I post my xorg.conf... Unfortunately it is quite confused, I suppose...

I had to comment all that lines with "modeline", otherwise at every reboot the definition was 640x480........



Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1280x1024 Laptop Display Panel"
	Horizsync	31.5-90.0
	Vertrefresh	59.0-75.0
	#  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	#  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	#  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	#  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	#  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
	#  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	#  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
	#  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	#  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
	#  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	#  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
	#  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1280x800@60"	"1440x900@75"	"1280x768@75"	"1440x900@60"	"1280x800@75"	"1600x1024@60"	"1280x720@60"	"1680x1050@60"	"1280x768@60"	"1680x1050@75"	"800x600@60"	"1920x1200@60"	"800x600@75"	"800x600@72"
	EndSubSection
EndSection

Section "Screen"
	#   
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x800@60"
	EndSubSection
EndSection

Section "ServerFlags"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


Thanks again and regards

H

---

### Post by Zorael on 2008-03-12
Curious!

I would suggest that you backup your xorg.conf, then reconfigure it to get the default settings. Note that the file will be overwritten.
```
$ sudo dpkg-reconfigure -phigh xorg.conf
```

Then have the Nvidia configurator set it up to get the correct driver entry, or just modify it yourself.
```
$ sudo nvidia-xconfig
```

If you want it to add the common Nvidia tweaks. Optional, of course.
```
$ sudo nvidia-xconfig -d 24 --composite --allow-glx-with-composite --add-argb-glx-visuals --render-accel
```
I think it can be entered as one line like that, else I guess this would work. Again, optional.
```
$ sudo nvidia-xconfig --composite
$ sudo nvidia-xconfig --render-accel
$ sudo nvidia-xconfig --allow-glx-with-composite
$ sudo nvidia-xconfig --add-argb-glx-visuals
```

And remove that **xserver-xgl** package if you have it installed.

---

### Post by herger on 2008-03-13
Hello! Here I am.
Unfortunately, no progress at all...

sudo dpkg-reconfigure -phigh xorg.conf
package 'xorg.conf' is not installed
/usr/sbin/dpkg-reconfigure: xorg.conf is not installed

Then, if I follow the other instructions You gave me, it says 
xorg.conf stored in xorg.conf.backup and rewritten, but if I try to enable desktop effects, always the yellow triangle with "desktop effetcs could not be enabled"....

I didn't say I am using Gutsy and Gnome environemnt.

Thanks and regards

H

---

### Post by herger on 2008-03-13
Here am I again.
I post the "new" xorg.conf file just below.
The resolution is ok, the only problem is still the enabling of desktop effects....


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"

	#  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	#  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	#  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	#  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	#  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
	#  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    Identifier     "Failsafe Monitor"
    VendorName     "Dell"
    ModelName      "Dell 1280x1024 Laptop Display Panel"
    HorizSync       31.5 - 90.0
    VertRefresh     59.0 - 75.0
    Gamma           1
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1280x800@60" "1440x900@75" "1280x768@75" "1440x900@60" "1280x800@75" "1600x1024@60" "1280x720@60" "1680x1050@60" "1280x768@60" "1680x1050@75" "800x600@60" "1920x1200@60" "800x600@75" "800x600@72"
    EndSubSection
EndSection

Section "Screen"

	#   
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x800@60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


Thenks and regards

Herger

---

### Post by herger on 2008-03-14
Hi all!
I found a topic on hoe to install nvidia dirvers:

[http://nonsolounix.wordpress.com/2007/11/17/driver-nvidia-ubuntu-gutsy-gibbon-appena-provati/](http://nonsolounix.wordpress.com/2007/11/17/driver-nvidia-ubuntu-gutsy-gibbon-appena-provati/)

Unfortunately it's in Italian, but I think it is quite understandable.

More unfortunately, at the end of everything, the compiz desktop cannot be enabled as usual....
Anyone can help?

Thanks and regards

Herger

---

### Post by herger on 2008-03-17
Hi all!
Excuse me, but can't anybody help me?
Thanks and regards

H

---

### Post by herger on 2008-04-20
Hi all.
I am really sorry, I couldn't fine anything that could help me in all these 4 weeks...
Does anybody know anything to make Compiz work on my Dell XPS 1330???
Thanks in advance and regards

Herger

---

