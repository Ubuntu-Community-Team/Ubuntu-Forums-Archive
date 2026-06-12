---
title: "Cannot login into Gnome"
date: 2006-11-04
forum: Desktop Environments
---

### Post by windz on 2006-11-04
I've just installed Edgy Eft on a Pentium III 667 MHz, 128 RAM, 3dfx Voodoo graphic card. The hard disk has an existing Windows partition and hda1, which I did not touch. hda2 is swap partition. hda3 is a 10GB reiserfs partition, on which Ubuntu is installed.

After installing I cannot log into Gnome from GDM. After entering username and password, gnome starts and and I get a glimpse of the desktop, before a black screen appears and then the login screen appears again.  

However I am able to log into Terminal failsave. From there, I can start Gnome by entering 'dbus-launch --exit-with-session gnome-session'. But the session only lasts for a while. In midst of running other application, for example, firefox and so on, the black screen will suddenly appear, followed by the login screen again. 

The only error messages in xsession-errors are concerning warnings that certain programs like update-notifer has been killed because X server has been killed/ disconnected or something like that. Xorg.0.log also shows no error messages other than those about wacom which I have rectified by editing xorg.conf.

Can anyone help, please?

---

### Post by amohanty on 2006-11-04
Try the following:
login into terminal
**startx**
at crash post the startx output

AM

---

### Post by windz on 2006-11-04
Thanks for the quick reply.

I logged into Terminal Failsave.

$startx

This is the output:

xauth: creating new authority file /home/*username*/.serverauth.4305
X: user not authorized to run the X server, aborting

---

### Post by windz on 2006-11-04
By the way, if I enter just 'gnome-session'  in Failsave Terminal Session, I get this output:

SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5431
(nautilus:5446): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.

(gnome-panel:5444) : libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

libnotify-Message: Unable to get session bus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

---

### Post by windz on 2006-11-04
Latest update:

I've finally found out what was wrong. The graphic card's driver 'tdfx' was causing X server to crash. After I replaced 'tdfx' with 'vesa' in xorg.conf, everything was ok. Of course, there is no 3D acceleration, and the display is not very nice. But at least I've found the source of the problem. 

Now: To try get tdfx to work. I've installed 'libglide3' but that didn't seem to work. X crashed again.

---

### Post by eb_oesch on 2006-11-04
> **windz said:**
> By the way, if I enter just 'gnome-session'  in Failsave Terminal Session, I get this output:

SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5431
(nautilus:5446): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.

(gnome-panel:5444) : libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

libnotify-Message: Unable to get session bus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

I get the same error, but my video driver is fglrx. The error  occurred after an "apt-get upgrade" that affected both the kernel and the fglrx driver.

The error manifests itself slightly differently for me, though. I get an infinite loop of "Bug buddy" popping up, and then when I dismiss it, popping up again.

I should probably add that Bug-buddy identifies /usr/bin/gnome-panel as the source of the problem.

---

### Post by amohanty on 2006-11-04
How about trying a:
sudo dpkg-reconfigure xserver-xorg 
and selecting the drivers, sometimes the upgrade screws up the xorg.conf file.

HTH
AM

---

### Post by windz on 2006-11-04
> **amohanty said:**
> How about trying a:
sudo dpkg-reconfigure xserver-xorg 
and selecting the drivers, sometimes the upgrade screws up the xorg.conf file.

HTH
AM

I have already tried that. The 'tdfx' driver simply does not work. Besides, the dpkg-reconfigure added entries regarding 'wacom' (eraser, cursor, stylus) which are redundant in my system, and the font paths were also configured wrongly where 'X11' and 'fonts' were in a reversed position, 

By the way, I did not upgrade the system from 6.06. It is a fresh installation on a partition where SuSE 9.3 was previously installed.

---

### Post by amohanty on 2006-11-04
Well thats pretty much the end of my knowledge well regarding X. Hopefully somebody else might be able to help you with the tdfx drivers.

AM

---

### Post by windz on 2006-11-05
> **amohanty said:**
> Well thats pretty much the end of my knowledge well regarding X. Hopefully somebody else might be able to help you with the tdfx drivers.

AM

Thanks anyway. At least now I know the source of the problem and don't have to fiddle around with the gnome / gdm configuration files. I've gone through the threads regarding tdfx driver and there are a couple of things that I could try. However the feedbacks from those threads are not very encouraging and I've found bug reports as well from people who are having the same problem as mine. So far no solutions have been given. Will leave a note here if I ever get it to work.

---

### Post by mooglie on 2006-11-09
I had the same problem with Edgy. I tryed to install Arch Linux and what???? Still the same problem with X. I found that it was caused by the tdfx driver and I found a fix:

[http://lists.freedesktop.org/archives/xorg/2006-August/017472.html](http://lists.freedesktop.org/archives/xorg/2006-August/017472.html)

With Arch, I recompiled the tdfx driver with the patch and now it works! I think I'll try Edgy on my desktop again! ;) By the way, is there an easy way to recompile source code on Ubuntu (to solve the problem)? ;)

Thanks

---

### Post by amohanty on 2006-11-12
No unless you download the source packages, and:
1. rebuild the deb
or 
2. use checkinstall instead of 'make install'

HTH
AM

---

### Post by mooglie on 2006-11-12
I rebuilt the .deb applying the patch I talked about! The tdfx driver now works! :)

---

### Post by eilker1917 on 2006-11-12
> **windz said:**
> Thanks for the quick reply.

I logged into Terminal Failsave.

$startx

This is the output:

xauth: creating new authority file /home/*username*/.serverauth.4305
X: user not authorized to run the X server, aborting

i have exactly same problem in kubuntu 6.06 /kde here not gnome/ . and newbie here...could you pls tell me for vesa thing, what to modify in xorg.conf ???

this is my xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by eilker1917 on 2006-11-13
> **eilker1917 said:**
> i have exactly same problem in kubuntu 6.06 /kde here not gnome/ . and newbie here...could you pls tell me for vesa thing, what to modify in xorg.conf ???

this is my xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


sometimes life is funny ](*,) 

i tried to solve that problem at least one week, i reconfigured every conf file in system,and i couldnt solve it, finally i left it.

today, at kde logging screen . from menu / connection type/ choosed kde, than no problem :)) ](*,)  ](*,)

---

### Post by travm on 2007-03-19
sorry to resurrect this thread, but I am having a problem with my voodoo 3 and the tdfx driver.  How do i patch my driver with this patch?  and frankly, where is the patch, is this it here

```
-- src/tdfx_priv.c.orig	2006-04-07 15:37:49.000000000 -0600
+++ src/tdfx_priv.c	2006-08-11 12:50:10.000000000 -0600
@@ -10,6 +10,9 @@
 #include "compiler.h"
 #include "tdfx.h"
 
+extern void xf86getsecs(long *, long *);
+#define getsecs(a, b)           xf86getsecs(a, b)
+
 /*
   Memory layout of card is as follows:
 
```

currently i am using the vesa driver, but i would like to get hardware accelleration working.
please help, I am new.

---

