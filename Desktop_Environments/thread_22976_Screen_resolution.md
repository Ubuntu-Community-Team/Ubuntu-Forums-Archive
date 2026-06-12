---
title: "Screen resolution"
date: 2005-03-30
forum: Desktop Environments
---

### Post by mirkaiser on 2005-03-30
Hi !!!!

I have some problems with Ubuntu 4.10!!!!
I have installed it on my laptop (HP zv5330ea) and it worked very welland the screen resolution was 1280x800@60,....
After the installation of several software (Amule,xine,xmms...) only using  apt-get, i have now only 640x480@60 screen resolution and it seems not possible to change it again.......

How can I solve my problem???

Thanks to everybody

---

### Post by arctic on 2005-03-30
please post the contents of your /etc/x11/xorg.conf file.

---

### Post by mirkaiser on 2005-03-31
[QUOTE=arctic]please post the contents of your /etc/x11/xorg.conf file.[/QUOTE]

I don't have xorg.conf file in that folder...are you sure that this file should exist?

---

### Post by wfx on 2005-03-31
[QUOTE=mirkaiser]I don't have xorg.conf file in that folder...are you sure that this file should exist?[/QUOTE]
/etc/**X11**/xorg.conf

---

### Post by hashimoto on 2005-03-31
On Warty you are running xfree86, not xorg. The location is the same, but the name is XF86Config-4 (if memory serves).

---

### Post by mirkaiser on 2005-03-31
[QUOTE=hashimoto]On Warty you are running xfree86, not xorg. The location is the same, but the name is XF86Config-4 (if memory serves).[/QUOTE]

In fact I have XF86Config-4...here it is:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	HorizSync	28-33
	VertRefresh	43-72
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by hashimoto on 2005-03-31
Check that the HorizSync and VertRefresh rates correspond to your display. You should find the data in the manuals (unless they are as useless as on my old Compaq laptop). Edit in the correct ones (you need the root rights). Some people seem to recommend that you comment out the lines alltogether, but somehow I don't like the idea.

Alternatively (and some say that this is the recommended way), you can run in terminal:
sudo dpkg-reconfigure xserver-xfree86
Have your specs available.

---

### Post by arctic on 2005-03-31
[QUOTE=wfx]/etc/**X11**/xorg.conf[/QUOTE]
doh! stupid typo i made... my apologies

---

### Post by mirkaiser on 2005-03-31
[QUOTE=hashimoto]Check that the HorizSync and VertRefresh rates correspond to your display. You should find the data in the manuals (unless they are as useless as on my old Compaq laptop). Edit in the correct ones (you need the root rights). Some people seem to recommend that you comment out the lines alltogether, but somehow I don't like the idea.

Alternatively (and some say that this is the recommended way), you can run in terminal:
sudo dpkg-reconfigure xserver-xfree86
Have your specs available.[/QUOTE]


Ok now it works properly....... thank you

---

