---
title: "aperture beyond 4gb. Ignoring"
date: 2009-02-15
forum: General Help
---

### Post by JimBuntu on 2009-02-15
Error: Aperture beyond 4gb. Ignoring.

This is an error that I'm getting upon start up with Ubu 8.10. Anyone know what it means. Didn't have it on 7.1.

---

### Post by drhex on 2009-02-15
I think the "aperture" is the range of memory addresses where video memory is mapped so it can be used by the CPU.

---

### Post by JimBuntu on 2009-02-16
Is there a reason why its saying that? And how do i fix? My compiz is not working at all right now and I'm thinking that its probly related to this.

---

### Post by crazyfuturamanoob on 2009-02-16
I get it too. There is no time to read it and I never write it down but it was something like this:
> 
Aperture beyond 4Gb, ignoring
BIOS doesn't leave memory hole
Please enable xxx in your BIOS
This will cost you 64mb RAM

Nothing related to compiz, I get it no matter if compiz is on or off. (and compiz works)

But that steals me 64Mb RAM, grr. System monitor shows only 3.9Gb, because of the evil bios.

---

### Post by Kevbert on 2009-02-16
General questions: How much memory do you have ? If you have more than 3.2Gb of memory and a 64 bit PC, are you using the 64 bit OS ? If you have a 32 bit PC, are you using the server version of Ubuntu as this supports more than 4Gb ? (PIA). 3.9Gb showing for a 4Gb install is about right.
On my 64 bit PC I have 4Gb and ```
free -m
``` shows 3956Mb.
JimBuntu - the compiz error is probably unrelated, what do you get if you enter
```
compiz
``` at the command line and what card are you using ?

---

### Post by JimBuntu on 2009-02-17
```
ubuntu@ubuntu-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
```

This is a laptop so the card is an integrated ATI. Everything worked properly with Ubu 7.1 Then I upgraded and now no compiz graphics.

---

### Post by crazyfuturamanoob on 2009-02-17
Yes, I got 64bit processor, 64bit Ubuntu 8.10, and 4Gb RAM. And free -m prints 3960.

Is server edition somehow different, other than it can use all memory?

---

### Post by JimBuntu on 2009-02-17
boomp (with an accent)

---

### Post by zika on 2009-02-17
> **JimBuntu said:**
> Error: Aperture beyond 4gb. Ignoring.
This is an error that I'm getting upon start up with Ubu 8.10. Anyone know what it means. Didn't have it on 7.1.
in /boot/grub/menu.lst change ```
gksudo gedit /boot/grub/menu.lst
``` the line beginning with (something like this, the first word is important)```
# defoptions=vga=788 splash
```into ```
# defoptions=vga=788 splash iommu=noaperture
```and then do ```
sudo update-grub
```[COLOR=MediumTurquoise]**please be sure that You know what You are doing since this file is essential for Your further use of Ubuntu.**[/COLOR]

---

### Post by Kevbert on 2009-02-18
crazyfuturamanoob. Server edition (32 bit) supports PAE (sorry I get the acronyms mixed up). So you can use more than 3,2Gb on a 32 bit machine with 32 bit operating system. You can read about it [[COLOR="Red"]here[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

JimBuntu. Please run [COLOR="Red"][compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check")[/COLOR] to see if that helps. If not please post your /etc/X11/xorg.conf file and what display adapter do you have ?

---

### Post by JimBuntu on 2009-02-18
For some reason all of the commands you guys have told me to run keep saying permission denied.

---

### Post by Kevbert on 2009-02-18
JimBuntu. Please go to Applications-Accessories-Terminal and enter
```
gedit /etc/X11/xorg.conf
```
Highlight the text displayed and press Ctrl-Shift-C (to copy it). Now open a new post and paste the text with Ctrl-V.
Sorry, if you mean the other commands, are you using 'sudo' to open the file prior to editing (by default you can't do this via the Nautilus filemanager) ? In the case of editing menu.lst the command would be
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by geirha on 2009-02-18
There's a bug report on this. Seems many people experience this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

---

### Post by Kevbert on 2009-02-18
The bug report is for anyone who gets the error message and has less than 4Gb.

---

### Post by zika on 2009-02-18
> **JimBuntu said:**
> For some reason all of the commands you guys have told me to run keep saying permission denied.
I've changed my post so that might help You. the first part is about editing the fie /boot/grub/menu.lst and the last is for applying that change. first and fourth "code" are for Terminal window. (Applications->System->Konsole) sudo puts You in a root "mode" (You will have appropriate permissions) so You have to enter appropriate password which will not be seen while You type it.

---

### Post by zika on 2009-02-18
> **Kevbert said:**
> The bug report is for anyone who gets the error message and has less than 4Gb.
I've been ignoring that bug since I have 3Gb. applying the patch I gave above solved many issues (even with graphics, speed, ...) I did not even thought might be related to that. strange ... ;)

---

### Post by Kevbert on 2009-02-18
> **zika said:**
> I've been ignoring that bug since I have 3Gb. applying the patch I gave above solved many issues (even with graphics, speed, ...) I did not even thought might be related to that. strange ... ;)

Thanks for that patch, as well as getting rid of the message, boot up times have improved. It doesn't seem to increase the memory reported by Ubuntu though.

---

### Post by JimBuntu on 2009-02-18
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

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"CoreKeyboard"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc104"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"stylus"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"eraser"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"cursor"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by Kevbert on 2009-02-18
You're going to love this... The ati driver was blacklisted due to problems.
To get compiz working you'll need to take a look at [[COLOR="Red"]this[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"). Before you try that see if when you do this you get the option to ignore checks. In terminal enter
```
compiz --replace
```

---

### Post by JimBuntu on 2009-02-18
Here's what I got with compiz --replace:

ubuntu@ubuntu-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

Tried the wiki stuff but still says composite extension not available. I think I'm just going to try to do a fresh reinstall of 8.10.

I have this on another thread but seem to have not gotten an answer: If I stick the disk with 8.10 in and reinstall will it just install over the current Ubuntu partition? I do not want it to erase the windows xp partition...

Thanks for everything!

---

### Post by zika on 2009-02-19
change```
Section "Extensions"
    Option        "Composite"    "0"
EndSection
``` in xorg.conf to```
Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
```__

---

### Post by dcstar on 2009-02-19
> **JimBuntu said:**
> Error: Aperture beyond 4gb. Ignoring.

This is an error that I'm getting upon start up with Ubu 8.10. Anyone know what it means. Didn't have it on 7.1.

It is a message about old AGP video hardware, and since most new hardware has PCI-E video hardware this message is unnecessary - and basically only worrying people - as for some reason the 8.10 kernels display it at boot-up.

---

