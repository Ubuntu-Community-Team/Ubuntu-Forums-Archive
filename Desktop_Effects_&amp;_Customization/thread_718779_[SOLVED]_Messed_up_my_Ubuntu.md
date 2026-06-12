---
title: "[SOLVED] Messed up my Ubuntu"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by pipesnipe on 2008-03-08
Ok, now I'm Sick of this!!!

My Ubuntu is totally messed up. Fonts are to big, borders are messy, desktop effects cannot be enabled, glinfo | grep rendering gives me direct rendering = no (Used to be yes just some hours ago),   resolution is bugged, ubuntu cannot detect the right settings for my screen, xorg.conf file is totally damaged (Don't have the same settings as it should be),

I decided to reformat and run a clean install of ubuntu, but wait... My Live-cd had just the same problems as told :mad:

Please, anyone have a solution to this???

---

### Post by boeing777 on 2008-03-08
what did you do to it?? did it just become like that for no reason?

---

### Post by pipesnipe on 2008-03-08
No.. It happened after trying to run multiple screens... After that, resolution was messed up... I tried all kinds of solutions... Fixed it... and now, EVERYTHING is messed up-...

But yes... of no reason.. I think

---

### Post by boeing777 on 2008-03-08
it's kind of weird, if you don't have to backup too much, i would just reinstall, it doesn't take long.

---

### Post by CREEPING DEATH on 2008-03-08
you could try the old ```
sudo dpkg-reconfigure xserver-xorg
``` and select the defaults and see what happens.  Were you manually editing the xorg configs?

CD

---

### Post by InfinityCircuit on 2008-03-08
You should post the output of "lspci -nn" to give us more information about your hardware.

---

### Post by pipesnipe on 2008-03-08
lspci -nn gave me this
> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)


Yes, I have tried to reconfigure xorg.conf... but I think that is the reason to why its messed up..
I've tried "sudo -regonfigure -phigh xserver-xorg too, and then startx... But this worked only the first 3 times...

---

### Post by pipesnipe on 2008-03-09
Here is my xorg.conf file..

Just in case...

> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Standard skjerm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Standard skjerm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by pipesnipe on 2008-03-10
Yay, I fixed it!

I'm not sure how, but i searched for the i810 driver, and found out that the driver was not supported by 7.10, and on the same page that they sais that, there was some configurations that I should put in my xorg.conf file...

I restarted, the xorg.conf file was reconfigured, added Composite disabled... Restarted... Changed it to enabled, And now, everything works again!!!

Except font size in login window... :(

I'm Back again!!! :lolflag:

---

