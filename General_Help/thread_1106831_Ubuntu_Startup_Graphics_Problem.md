---
title: "Ubuntu Startup Graphics Problem"
date: 2009-03-26
forum: General Help
---

### Post by h2o4444 on 2009-03-26
I just installed Ubuntu 8.10 on my laptop as the sole operating system. But I noticed after a few startups/shutdowns Ubuntu doesn't startup correctly.

The problem is when I turn on the computer and the screen stays black. No BIOS, no HP startup logo, no nothing. This morning I had to restart manually about 5-6 times before Ubuntu can finally load. When it does load, at times, it loads to a screen that is darkened or dimmed, with an error message that I can only partially read because the message goes off to the side and out of view. The message basically says that Ubuntu cannot detect the correct graphics card and I need to do at manually.

The problem gets temporarily "fixed" when I restart the computer manually by switching on/off with the power button enough times that Ubuntu loads normally. I don't think this is a good way to startup my computer. Does anyone else experience this or is it just me? And how should I fix it, I consider myself a newbie so I don't know much about the command line, or should I wait for 9.04 and hope the problem will get fixed on its own?

Thanks in advance.

---

### Post by Jimmyfj on 2009-03-26
What type is your graphics adapter? Is it ATI or nVidia ? That's importend to know before we can find any solution. At the same time the main specs of the laptop would tell of where to look for errors.

---

### Post by h2o4444 on 2009-03-26
The graphic card is Intel Graphics Media Accelerator (GMA) 900 and the computer is an HP Compaq tc4200. Here's the main specs:

# Processor Speed: 1.86 GHz
# RAM: 512 MB
# Weight: 4.6 lb
# Screen Size: 12.1 inches
# Graphics Card: Intel Graphics Media Accelerator 900 GM
# Storage Capacity: 60 GB
# Networking Options: 802.11g
# Primary Optical Drive: External

---

### Post by furcino on 2009-03-26
I do not know whether this really is an Ubuntu problem since you said that Bios does not appear either... But there are a few things you should try out:

1. Try to get into your Bios and set default factory settings
2. Check the other information in Bios and make sure the settings are correct (for example my Ubuntu would not start up, because in Bios I had a floppy installed and in reality there was none so Ubuntu kept looping endlessly on startup)

Also... are you sure your bios does not appear on start-up or is it just because the monitor isn't catching up with the bios? Try starting and if you do not see the bios, restart. If the bios is up there it should be alright and then you should start focusing on Ubuntu.

---

### Post by furcino on 2009-03-26
Also... did you have the same problem with the OS you had before ?

---

### Post by h2o4444 on 2009-03-26
Changing BIOS to default is something I should do since I changed it to boot from an external DVD drive first so I can install Ubuntu from a CD and never thought to change back to default.

As to the question of whether the BIOS is not loading or not seen, I'm just as puzzled as you are.

Lastly, I did not have this problem with the OS (Windows XP Tablet Edition) I had before, probably because I never had to change the BIOS.

Now that I changed the BIOS to default I think everything should work fine.

Thank you very much!

---

### Post by h2o4444 on 2009-03-26
As it turns out, the problem still persists after I changed the BIOS to its default setting.

The problem is this, still:

When I turn on the computer, it starts out dimmed, so dimmed that I can only barely see the large HP logo at the startup and I can't see anything else.

Then I press and hold the power button to force shutdown and restart the whole thing. When I do this several times the machine then finally loads correctly, but only after an off-to-the-side-partial display saying that something to the effect the graphics driver is faulty.

I'm not sure if this is a display problem of the computer or if it's the Ubuntu software. Maybe it's a combination, because the LCD display does flickers once in awhile. Also the computer was made in 2005 and has a tablet LCD.

Anyways, any help is still appreciated.
Thanks in advance.

---

### Post by Favux on 2009-03-26
Hi h2o4444,

Hope it's not a hardware issue.  I'll attach a xorg.conf that seems to have worked for others.  And here is a thread I hope you find useful:

[http://ubuntuforums.org/showthread.php?t=1027808]("http://ubuntuforums.org/showthread.php?t=1027808")

peterlustig put a lot of time and effort into his installation HOW TO.  So please read it over before doing anything.

Hope this helps.

---

### Post by h2o4444 on 2009-03-27
Dear Favus,

Thank you for the xorg.conf.txt file. A few months ago when I first installed Ubuntu I spent two days editing the xorg.conf file under /etc/X11 for the tablet functions. I'm comparing the your xorg.config file and the current one I have (see below) and I think both are essentially the same. So I don't know if it's the file that's messing things up.

> # xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
EndSection

---

### Post by Favux on 2009-03-27
Hi h2o4444,

You are correct, they are essentially the same.  Except yours is missing a video section (below the last wacom entry and above the "Monitor" section):
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
this is the same section you would identify your video card with like:
```
	Driver		"nvidia"
```
or ATI or Intel, etc.  Which you don't need, I suppose because yours runs on the default Xorg Intel driver.

In addition the xorg.conf I gave you assumes the wacom symlinks are in place and doesn't use the "/dev/ttyS0" path.

Since you're running 8.10 you can comment out the keyboard, mouse, and Synaptic touchpad and HAL (hardware abstraction layer) will run them for you through it's .fdi files rather than xorg.conf.  Just be sure you comment out Synaptics in "ServerLayout" too.

Hopes this helps.

---

