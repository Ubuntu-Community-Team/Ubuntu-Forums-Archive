---
title: "Beryl why do you hate me so!"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by ericdegen on 2007-05-23
Ok so I'm running Feisty on two machines, one has Beryl up and all happy (Nvidia 6600) the other is my notebook with an ATI x1600 and regradless of how many helps I use there is just no joy.  Beryl is installed, but when I try to "select" it as my window manager the screen just flickers and then reverts back to the Gnome default.

I'm running the ATI proprietary driver, my fglrxinfo displays as follows:

eric@elinux:~$ fglrxinfodisplay: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)
 
Next is my xorg.conf:


Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

I have tried several Howtos and worked on this for about two weeks, Im really quite frustrated.  This is on an HP NC8430 notebook, Integrated PCIe ATI X1600 256MB.

Any help would be awesome!

---

### Post by dxdemetriou on 2007-05-23
Option "Composite" "0"
You have the composite disable
I am not sure for others, here is mine

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection

Try to change the "0" to "1"

You know how to use command line if X11 don't start, right?

---

### Post by ericdegen on 2007-05-24
Thanks for the input dxdemetriou, I'll give it a try and post back.  

I went with the Composite = 0 or disabled, based on advice from other posts that the ATI's don't support it, but I'll change that and the Render mode.

---

### Post by ericdegen on 2007-05-24
No change, with those lines added. Still flickers when I try to engage  Beryl and reverts back to the Gnome default. Thanks anyway.

---

### Post by patrickfromspain on 2007-05-24
With an Ati card, you must setup XGL X server:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by ericdegen on 2007-05-26
Thanks Patrick! I had followed this guide before, but missed the final step where you set XGL as the default session manager, pasting this in for others below.  It's kinda tricky as I did not have to do this for my other Nvidia box.

** Changing your standard login**

ONLY DO THIS IF YOU DIDN'T ADD AN XGL SESSION TO GDM PER THE PREVIOUS SECTION!!! You only need one or the other.

For GNOME: Instead of adding a separate desktop session, you could alter your standard X session. This is not recommended for most users (see above). It might be useful however if you do not want to set up a separate X session for Beryl for some reason.

First change gdm.conf-custom:

$ sudo nano /etc/gdm/gdm.conf-custom

Go to the very bottom of the file and add:

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

When you reboot or restart the graphical session, the Xgl server should be running.

---

### Post by jesnev on 2007-10-02
The link does not work, 404 error. Any cure for that?
/jesnev

---

