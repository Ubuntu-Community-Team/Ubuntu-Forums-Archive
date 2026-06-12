---
title: "Screensaver issues with (ATI restricted driver + xgl)"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by riverfr0zen on 2007-10-20
Running Gutsy, with xserver-xgl and ATI restricted driver - the effects work great. However, the screensaver does not work at all. Furthermore, the monitor goes blank/black after 10-15 of idle time, which is really annoying if you're watching video.

I saw a bunch of other posts describing this problem, and offering some meager solutions for Feisty, but are there any solutions for Gutsy? 

Ideally, the system would adhere to the Gnome screensaver settings - is this possible?

---

### Post by benfortuna on 2007-10-22
I have the same problem with ATI Radeon 9600. This bug is the closest I could find to this issue:

[https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/33717](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/33717)

---

### Post by keenish27 on 2007-10-22
just paste this code to the bottom of your xorg.conf file

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "20"
EndSection

this will tell the monitor to shut off after 20 min

---

### Post by cliss on 2007-10-22
That's helpful, but the idea is not to shut the monitor off, but instead to display the screen saver.

If I'm reading this correctly, the screen saver is being displayed on display :0 when it needs to be on display :1?  If so, is there a way in which to "move" it?

> **keenish27 said:**
> just paste this code to the bottom of your xorg.conf file

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "20"
EndSection

this will tell the monitor to shut off after 20 min

---

### Post by keenish27 on 2007-10-23
I'm sorry, i should have explained that more.

Your screen saver is actually turning on, but the power saving values are always set to give you a blank screen at 10 min.  changing the options in power saving options has no effect on when your screen shuts off and what not.  Thats why you need to add this to your xorg.conf.

you just need to edit the values there.

i have my screen saver set to come on at 10 min then the screen to shut off at 20 min.  if you want your screen to always be on just change the 20 to a 0 so that it looks like this 

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

this way your screen will never turn off and your screen saver will have time to display.

---

### Post by cliss on 2007-10-23
Thanks for the expanded explanation.  However, I have two issues/questions:
[LIST=1]
[*]Adding that section to the end of my config slaughtered X windows... I couldn't start it, amongst other errors.
[*]Why can't I see my screensaver when I have the timeout set to only 1 minute, before these config changes?
[/LIST]

Thanks for the help!

> **keenish27 said:**
> I'm sorry, i should have explained that more.

Your screen saver is actually turning on, but the power saving values are always set to give you a blank screen at 10 min.  changing the options in power saving options has no effect on when your screen shuts off and what not.  Thats why you need to add this to your xorg.conf.

you just need to edit the values there.

i have my screen saver set to come on at 10 min then the screen to shut off at 20 min.  if you want your screen to always be on just change the 20 to a 0 so that it looks like this 

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

this way your screen will never turn off and your screen saver will have time to display.

---

### Post by keenish27 on 2007-10-23
well as for this killing our xserve, i'm not sure why it did that.  i have it in mine and everything is working fine.  maybe some of the character didn't copy correctly (i've had that happen before and my xserve wouldn't start at all)?

I'm not sure why ur screen saver doesn't work at all.  Does the preview work?

i'd be happy to post my xorg.conf if it will help ya.

---

### Post by cliss on 2007-10-23
To be fair, I could still run X, but in "reduced graphics" mode (what looked to be 640x480 instead of my usual 1400x1050).

I can see the previews, even full-screen previews.  The problem lies in seeing screensavers outside of the previews.  :)

Below is my [FONT="Courier New"]xorg.conf[/FONT] for reference.  Note your recommended changes are not included; this is the conf i'm running as I type.

Thanks again for all the help.  It's really appreciated. :)

```
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
        Option          "EmulateWheel"  "true"
        Option          "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
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
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection
```

---

### Post by MothMonsterman on 2007-10-23
I am also using the ATI restricted driver, compiz-fusion, and xserver-xgl, and having the same problems. Screensavers only work if I put them on "locked" mode,  and without these config changes my screen will turn off in around 10 minutes automatically.

---

### Post by cliss on 2007-10-23
> **MothMonsterman said:**
> Screensavers only work if I put them on "locked" mode

Interesting, I never noticed that, but mine also work when in locked mode.  Well, the one time I tried it so far I had to hit the [FONT="Courier New"]Cancel[/FONT] button, because when the screen saver started it immediately cancelled itself as though the mouse was moved.  However, after that it worked fine.

---

### Post by keenish27 on 2007-10-24
try changing

Section "Extensions"
	Option		"Composite"	"1"
EndSection

to

Section "Extensions"
	Option		"Composite"	"0"
EndSection


I know that my xorg is like that.  i'm on my windows machine at the moment though so I can't post it.

---

### Post by cliss on 2007-10-24
That was requisite to get Compiz working though!  :-?

---

### Post by riverfr0zen on 2007-10-27
Ha. I didn't subscribe to this thread, and so totally forgot I had started it.

Anyway, to follow up, I still haven't found a way to fix this issue. The following bug thread is  somewhat informational. The issue does appear to be XGL running on :1 instead of :0. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947)

I've been using the xset command mentioned in that thread to toggle screen blanking - useful if trying to watch a movie or something. But certainly not the desired solution. 

Getting the screensaver to work on :1 seems like a good goal, but don't know how either.

It's a shame, because other than that, XGL works very nicely until the ATI drivers are fixed up for AIGLX. Anyone else have any ideas?

---

### Post by riverfr0zen on 2007-10-28
Looked a little more into getting the screensaver to work. Through various forum threads and such, including the following:


[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/35501](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/35501)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947)

I think I've come up with a workaround (albeit a total hack). Essentially involves 

1) disabling the screen blanking. From the command line:
xset -d :0 s 0

2) Starting gnome-screensaver with the following options (again from the command line):
killall gnome-screensaver
gnome-screensaver --display=:0

This should get the screensaver to display as per your gnome screensaver settings. Now, of course, it would be annoying to do this every time you start your desktop. In that order, the following solution seems to work nicely for me. PLEASE NOTE: This is a total hack, and not the preferred way to go about this. I'm not too familiar with gnome startup, and how to change that, and that's why I'm doing this. If you don't understand what's being done, you should probably NOT do this.

1) Rename the actual gnome-screensaver program to something else:

sudo mv /usr/bin/gnome-screensaver /usr/bin/gnome-screensaver-actual

2) Write a script standing in gnome-screensaver's place that essentially does what is described above. Open up your favorite editor, and write to /usr/bin/gnome-screensaver (don't forget sudo). E.g.

sudo vi /usr/bin/gnome-screensaver

```

#!/bin/bash
/usr/bin/xset -d :0 s 0
/usr/bin/gnome-screensaver-actual --display=:0

```

3) Apply exec. perms:

sudo chmod 755 /usr/bin/gnome-screensaver

That should be it. Restart your xserver, and screensavers should work as normal (well, they do for me, at least). If anyone can suggest the *proper* way to go about doing this, it would be much appreciated.

---

### Post by MilitantPotato on 2007-10-28
Great work man. 
Both my wife's and my pc goes blank after 10 mins.  Makes it a pain to watch movies.

I'll try it on her computer first, in case it breaks something. :)

---

### Post by louvros10 on 2007-10-28
I can't open this file...!!! Problem with the encoding...
What should I do???

---

### Post by cliss on 2007-10-28
As an alternative workaround/hack, I stumbled upon [this thread]("http://ubuntuforums.org/showthread.php?t=195557"), which discusses how to use the executable [FONT="Courier New"]xscreensaver[/FONT] instead of [FONT="Courier New"]gnome-screensaver[/FONT].  This fixed my problems, and although I don't like the setup UI as much as [FONT="Courier New"]gnome-screensaver[/FONT], it is working better for me.

---

### Post by be4truth on 2008-02-03
I have the same problem on an Intel 965 graphic chip.

---

### Post by shadowplane676 on 2008-02-08
im wondering about this issue as well. i have Feisty Kubuntu with ATI FGLRX and XGL running Compiz Fusion. i have some screensavers that wont work with XGL/CF but Euphoria works (the one i want) in test mode, but doesnt kick in after the aloted time. Xorg.conf has my display as display 0 so *shrug* CF is working spectacularly, and my ATI chipset seems to be working fine. is this just a screensaver misdirection to a wrong screen as they worked fine in a regular KDE session.

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "dvorak"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "false"
EndSection




```

---

