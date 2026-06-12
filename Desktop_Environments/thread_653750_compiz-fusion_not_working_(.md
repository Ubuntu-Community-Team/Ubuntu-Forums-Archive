---
title: "compiz-fusion not working :("
date: 2007-12-30
forum: Desktop Environments
---

### Post by querulousennui on 2007-12-30
Hi, I'm new with Ubuntu and I'm trying to get compiz-fusion to work. (I previously had beryl and had unresolved problems with that too.)
I have 7.10 and Dell Latitude d600.

In the terminal, compiz results this:
Checking for Xgl: no present.
Detected PCI ID for VGA: 01:00.0 0300:1002:4c66 (rev 02) (prog-if 00 [VGA])
          Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, la
tency 32, IRQ 11
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: usr/bin/metacity

lspci | grep VGA returns:
\01:00.0 VGA compatible controller: ATI Technologies Radeon RV250 [Mobility FireGL 9000] (rev 02)


using SKIP_CHECKS=yes compiz does make it run, sorta, but it i can't see anything or work with anything, so it's useless to me.
This command returns:
Checking for Xgl: no present.
Detected PCI ID for VGA: 01:00.0 0300:1002:4c66 (rev 02) (prog-if 00 [VGA])
          Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, la
tency 32, IRQ 11
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply
. Possible causes include: the remote application did not send a reply, the mess
age bus security policy blocked the reply, the reply timeout expired, or the net
work connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'


Help is much appreciated! Thanks!

---

### Post by Perpetual on 2007-12-30
Hmm, I have a Dell D600 also with the Radeon Mobility 9200 card and Compiz-Fusion works straight out of the box with no configuring.  Other Distributions also work, Fedora, OpenSuSE, Mandriva, PCLOS and Debian (with some other packages I have to install).

Can you post your xorg.conf?

```
sudo gedit /etc/X11/xorg.conf
```

Did you install any drivers for your card?  Like I said, mine works out of the box without any special drivers.  Following is my xorg.conf

```

Section "Files"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

And when I run Compiz frum a terminal

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

```

Finally, have you tried enabling Compiz from System > Preferences > Appearance > Visual Effects?  When I ran Compiz from the terminal to post my results, I had to ctrl+alt+backspace to get my window borders back.  Apparently Compiz didn't like starting that way.  Also, install CCSM

```
sudo apt-get install compizconfig-settings-manager
```

Once CCSM is installed, trying disabling dbus from CCSM and see what happens.  I do have dbus enabled on my end.

[IMG]http://farm3.static.flickr.com/2339/2149407144_590ed17cb2.jpg[/IMG]

---

### Post by querulousennui on 2007-12-30
Compiz-fusion works fine for me under 1024x768, but I was hoping to use 1400x1050. I had tried to change my X11 config file to depth of 16 instead of 24, but that killed the config file and I had to change it back in order for my computer to work. 
Do you have an idea of how to use Compiz-fusion with 1400x1050?

Thanks!

---

### Post by Perpetual on 2007-12-30
The D600 does not support 1400 x 1050.  Are you using an external monitor? 

Edit: above is true with the XGA (which I have) and the SXGA D600 can do 1440 x 1050.  I would guess you have XGA also...

---

### Post by querulousennui on 2007-12-30
I'm not using an external monitor. How would I see if I'm using XGA vs SXGA? I haven't done anything to change the screen resolutions (other than use the pre-selected ones under System-->Preferences-->Screen Resolution). 1400x1050 comes up and I like that one. Is it possible to use that with Compiz-fusion?
Thanks!
EDIT:
I disabled the dbus. I am able to use the rotating cube, but some of the transparencies don't work (ie dropdownmenu transparency)

Thanks for your help!

---

### Post by Riel on 2008-01-02
The resolution is the problem. When setting resolution to 1024 all works quite fine.

I'll try disabling dbus and check if it will run on 1400 resolution too (SXGA indeed)
But with no other ati drivers installed (thus out of the box), is compiz hardware-accelerated?

---

