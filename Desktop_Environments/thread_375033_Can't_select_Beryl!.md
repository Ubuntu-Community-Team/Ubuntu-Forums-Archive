---
title: "Can't select Beryl!"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Dubtech on 2007-03-03
After a while of trying to pimp my laptop (A Dell Inspiron 9400 with a Intel 945GM card running Dapper) with Beryl, I'm stuck at the final point. When I run Beryl-manager, I can't select Beryl as my window manager. If I try to, it selects Compiz instead, and all my titlebars disappear and I can't select workspaces. I'm just wondering if I've missed out something somewhere, or I've screwed everything up? I will post my xorg.conf if it can help at all.

Any help would be greatly appreciated! :)

---

### Post by Kateikyoushi on 2007-03-03
Do you have xgl installed ? Posting your xorg.conf could help.

---

### Post by tubasoldier on 2007-03-04
same thing happened to me. I removed the beryl sources from my sources.list and then added in beryl-svn sources. After an apt-get update and an apt-get upgrade things work well for me. Even in KDE

---

### Post by Dubtech on 2007-03-07
Sorry for not replying - I've been away.

Anyway , when I got home last night, I upgraded mu Dapper to Edgy, as I've heard that Beryl is easier to install + works better on it. I uninstalled Beryl and Compiz and just reinstalled Beryl. Now when I run Beryl-Manager, it selects Metacity and displays this in terminal:

```
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwallpaper.so' plugin
beryl: No GLXFBConfig for default depth, falling back on visinfo.

** (beryl-manager:6972): WARNING **: Beryl caught deadly signal 8
```


[quote=Kateikyoushi]Do you have xgl installed ? Posting your xorg.conf could help.[/quote]

I don't think so since Edgy has pre-installed AIGLX. But here's my Xorg.conf anyway:

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
        Load    "dbe"
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller
        Driver          "vesa"
	BusID		"PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps"        
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
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

Section "Extensions"
        Option          "Composite"  "Enable"
EndSection
```

[QUOTE=tubasoldier]I removed the beryl sources from my sources.list and then added in beryl-svn sources[/quote]

I think I have the Beryl-svn sources already...

I'm starting to think it might be a problem with the installation, still, any help is great!

---

