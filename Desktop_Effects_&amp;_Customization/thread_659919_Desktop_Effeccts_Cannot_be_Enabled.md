---
title: "Desktop Effeccts Cannot be Enabled"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by phmcguin on 2008-01-06
Hi,

I've been trying to get desktop effects enabled. I'm using an nVidia NV15 [GeForce2 GTS/Pro] backed by 392MB RAM with a 850Mhz pentium. firstly, is this sufficient hardware to enable desktop effects?

I've installed drivers for my graphics card but how can I check if it's working correctly?

What steps do I need to take to enable desktop effects?

IIf I type compiz this is the output:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0150 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity 

I'm not sure if that's relevant. I read it in another post.

Thanks in advance, Please help I'm a newbie.

---

### Post by phmcguin on 2008-01-06
I tired installing XGL server but on a reboot I couldn't log back on.After logging in the login screen would just loop back after a splash screen showing the nVidea logo.I had to change the session to Gnome Safe. So I've un-installed it. and now I can log in using session as Gnome

---

### Post by sowelie on 2008-01-06
With nvidia you don't need xgl.  All you need is the proper nvidia drivers.  Have you installed the non free drivers?  To do this you execute:
```
sudo aptitude install nvidia-glx-new
```

Also, to check if your drivers are working properly execute the following command:
```
glxinfo | grep direct
```

If it says "Direct rendering: Yes", you're all set.  If not, your drivers are not installed properly.

Also, your system specs should be more than enough for the desktop effects.

---

### Post by r41nz0r on 2008-01-06
Go to System>Administration>Restricted Drivers Manager and make sure you have your restricted drivers enabled.

---

### Post by phmcguin on 2008-01-06
Thanks for the replies. 

1. I have restricted drivers enabled in the Restricted Drivers Manager.

2. I ran sudo aptitude install nvidia-glx-new Output is inluded below. It seemed to install the correct drivers.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libglitz-glx1 libglitz1 
The following packages will be automatically REMOVED:
  nvidia-glx-legacy 
The following NEW packages will be installed:
  nvidia-glx-new 
The following packages will be REMOVED:
  nvidia-glx-legacy 
0 packages upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 5014kB of archives. After unpacking 4846kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) gutsy-updates/restricted nvidia-glx-new 100.14.19+2.6.22.4-14.10 [5014kB]
Fetched 5014kB in 47s (105kB/s)                                                 
(Reading database ... 103327 files and directories currently installed.)
Removing libglitz-glx1 ...
Removing libglitz1 ...
Removing nvidia-glx-legacy ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 103267 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb) ...
Setting up nvidia-glx-new (100.14.19+2.6.22.4-14.10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

3. But after using glxinfo | grep direct I get:

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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Any help on this is greatly appreciated. Thank you so much for the posts so far.

---

### Post by snickers295 on 2008-01-06
i have the same problem, i have the nvidia-glx-new enabled and all the restricted drivers and it just says "Desktop Effects Could Not Be Enabled".

---

### Post by phmcguin on 2008-01-06
I've been trying to do some debugging but I'm very lost and have no real idea of what I'm doing.

If anyone has any idea of a solution or where to find a solution it would be a huge help.

---

### Post by phmcguin on 2008-01-06
Anything? Someone must have some ideas please?

---

### Post by sowelie on 2008-01-07
I think your problem may be with your xorg.conf.

```
Section "Device"
	...
	Option		"AddARGBVisuals"	"True"
	...
EndSection
```

Specifically make sure the AddARGBVisuals option is under the device section.  Also, make sure this is somewhere in the file (should be at the end):

```
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Once you have made these changes you'll have to restart GDM, you can do this by hitting CTRL+ALT+BACKSPACE.

---

### Post by snickers295 on 2008-01-07
> **sowelie said:**
> I think your problem may be with your xorg.conf.

```
Section "Device"
    ...
    Option        "AddARGBVisuals"    "True"
    ...
EndSection
```Specifically make sure the AddARGBVisuals option is under the device section.  Also, make sure this is somewhere in the file (should be at the end):

```
Section "Module"
    Load        "glx"
EndSection
Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
```Once you have made these changes you'll have to restart GDM, you can do this by hitting CTRL+ALT+BACKSPACE.
still no good.
does this look right to you:```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "compaqik13"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Boardname    "NVIDIA GeForce2 DDR (generic)"
    Busid        "PCI:0:9:0"
    Driver        "nvidia"
    Screen    0
    Vendorname    "NVIDIA"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Vendorname    "Gateway"
    Modelname    "Gateway EV500"
    Horizsync    30.0-70.0
    Vertrefresh    50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1400    1050
        Modes        "1280x1024@60"    "1400x1050@60"    "1280x960@60"    "1152x864@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection
Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
Section "device" #  
    Identifier    "device1"
    Boardname    "NVIDIA GeForce2 DDR (generic)"
    Busid        "PCI:0:9:0"
    Driver        "nv"
    Screen    1
    Vendorname    "NVIDIA"
EndSection
Section "screen" #  
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" #  
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by FuturePilot on 2008-01-07
> **snickers295 said:**
> i have the same problem, i have the nvidia-glx-new enabled and all the restricted drivers and it just says "Desktop Effects Could Not Be Enabled".
What Nvidia card do you have?

> **phmcguin said:**
> Anything? Someone must have some ideas please?
I'm fairly sure that your card isn't supported by the nvidia-glx-new driver. By your other post it looks like the Restricted Driver Manager installed the nvidia-glx-legacy. If this is the case then your card is not supported by the nvidia-glx-new driver. The Legacy driver is not capable of compositing.

---

### Post by phmcguin on 2008-01-07
I'm making progress. But I still need some help. I've no got the correct drivers installed and my card is working correctly. I can now see screensavers! But still no desktop effects :confused:

```
glxinfo | grep direct
direct rendering: Yes
```

--this looks good. 

```
compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0150 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

But compiz only get this far then hangs! If I use SKIP_CHECKS=yes COMPIZ
it crashes the GUI and I can just see my desktop without toolbars or anything.

Output of my xorg.conf is:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce2 DDR (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer V771"
	Horizsync	30.0-72.0
	Vertrefresh	50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@85"	"1024x768@75"	"832x624@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"1024x768@43"	"800x600@75"	"1152x864@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@85"	"1400x1050@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
```

any ideas on how to get desktop effects working?

thanks in advance. I'm really stuck on this.

---

### Post by sowelie on 2008-01-07
Hmm...that should be fine, but there are some extra sections at the bottom.  I would try starting from scratch.  You can do this by executing the following command:

```
sudo nvidia-xconfig
```

This will write the recommended settings to your xorg.conf file. It also makes a backup in case something goes wrong.  Once again make sure and restart GDM by hitting CTRL+ALT+BACKSPACE.

---

### Post by snickers295 on 2008-01-07
i got it working.
```
sudo apt-get install xserver-xgl
```
and then reset x then login with the "run xscripts" session and then the effects enabled.

---

### Post by phmcguin on 2008-01-07
thanks for posting that But...

```
$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

```

am I missing something?

---

### Post by sowelie on 2008-01-07
That's odd, do you have the nvidia-glx-new package installed?

Also, I've found that envy works really well.  It installs the newest nvidia drivers and configures everything for you.  There's a deb package you can just download and install [here]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu5_all.deb").   Once that is installed just run envy by going to applications -> system tools -> envy.

---

### Post by phmcguin on 2008-01-07
How do I check for that package??

Also, I've just tried to install envy and it throws an "Archive error" when trying to install dependencies. 

I can't believe it's taking so much to get my graphics card working enough to enable desktop effects

---

### Post by snickers295 on 2008-01-07
> **phmcguin said:**
> How do I check for that package??

Also, I've just tried to install envy and it throws an "Archive error" when trying to install dependencies. 

I can't believe it's taking so much to get my graphics card working enough to enable desktop effects
sudo apt-get install it
if it says its available to install, install it or it will say if you already have it or look thought the package manager for it

---

### Post by phmcguin on 2008-01-07
Ok..I just did a check and I don't have it. I have nvidia-glx-legacy...which I think is correct. Are you sure I should be using nvidia-glx-new?

---

### Post by FuturePilot on 2008-01-07
> **phmcguin said:**
> Ok..I just did a check and I don't have it. I have nvidia-glx-legacy...which I think is correct. Are you sure I should be using nvidia-glx-new?

If the Restricted Driver Manager installed the Legacy driver then it got it correct. Your card is most likely not supported by the nvidia-glx-new driver. Compiz will not work with the Legacy driver because it is not capable of compositing. You would most likely need to install XGL if you want to use Compiz

---

### Post by sowelie on 2008-01-07
I didn't realize that there was a separate package for the older nvidia cards.  Did you have any luck with XGL?  I had it up and running on an ATI Radeon 9600 at one point, it worked pretty well.

---

### Post by snickers295 on 2008-01-07
when i installed xgl,  my opengl driver messed up and i couldn't play my games on cedega.

---

### Post by phmcguin on 2008-01-08
from the forum I've understood that nVidia cards don't need XGL?

When I tried installing XGL a way back it messed up GNOME and I couldn't log into GNOME. so I had to uninstall it to be able to log in again.

---

