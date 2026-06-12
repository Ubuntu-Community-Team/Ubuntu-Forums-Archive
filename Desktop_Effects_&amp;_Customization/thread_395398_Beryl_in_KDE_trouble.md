---
title: "Beryl in KDE trouble"
date: 2007-03-28
forum: Desktop Effects &amp; Customization
---

### Post by richbiskit on 2007-03-28
I had beryl working perfect on ubuntu edgy, i got the kde desktop installed and beryl wont work but only in kde session, if i log bake into gnome session it works fine.

First i got this....

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048

beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0


so then i did killall kdesktop and started beryl again from the terminal, the result....

i loose my desktop background, i cant right click on the desktop, i loose all the window boarders (minimize, close etc), when i minimize a window i cant see it in the panel.

The cube works but without my desktop background.

i am using intel i810

THIS ONLY HAPPENS IN KDE SESSION, in gnome session it works perfectly!

Please help!!!!

---

### Post by richbiskit on 2007-03-28
Realy need help here guys!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I have searched the forums but everyone is talking about Nvida or ATI not intel:( 

This is my xorg.conf.... 

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by asimon on 2007-03-31
> **richbiskit said:**
> 
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

This is because KDE's window manager kwin is already running. Try to start beryl with 'beryl --replace'.

> **richbiskit said:**
> 
so then i did killall kdesktop and started beryl again from the terminal, the result....

i loose my desktop background, i cant right click on the desktop, i loose all the window boarders (minimize, close etc), when i minimize a window i cant see it in the panel.

The cube works but without my desktop background.

This is expected. If you kill kdesktop you loose the background, menu, and desktop icons, because they are all managed by kdesktop.

I am disappointed after trying beryl under KDE, there are some nice effects but it's a usability nightmare and my productivity with beryl dropped to zero (I was not even able to set shortcuts for switching desktops under beryl). Currently beryl is very very far away from a smooth integration into KDE.

---

### Post by wxnker on 2007-04-16
> I am disappointed after trying beryl under KDE, there are some nice effects but it's a usability nightmare and my productivity with beryl dropped to zero (I was not even able to set shortcuts for switching desktops under beryl). Currently beryl is very very far away from a smooth integration into KDE.

I've been using Beryl with Kubuntu and Mandriva KDE for some time now. Everything works perfect. No problems. So I do not recognize any of the problems you mention. Beryl and KDE works great for me.

---

### Post by Clay_Banger on 2007-04-19
try this:

back up your xorg.conf file.
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
```
open xorg.conf for editing
```
sudo kate xorg.conf
```
and make the modules section look like this:
```
Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "dbe"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "type1"
  Load "vbe"
EndSection
```
then restart the xserver (logout, select restart x  server on the menu)


if it doesnt work, restore your old xorg.conf
```
cd /etc/X11
sudo rm xorg.conf
sudo mv xorg.conf.bak xorg.conf
```
then restart

---

