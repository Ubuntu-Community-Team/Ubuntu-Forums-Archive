---
title: "Bad Gnome performance?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by xsence on 2005-10-23
I have a 2.2ghz amd xp with 2x 512mb dual channel pc3200 memory, 160gb sata and a nvidia 5700.

Is it normal that windows xp pro works much faster then this system running breezy ubuntu?

---

### Post by mulperi on 2005-10-23
In my opinion it is normal, however you get more bang for the bucks with Ubuntu!

Try installing nvidia drivers for your graphics card, if you haven't done that already. You could also try initng to make booting times shorter. For some reason I cannot get ALSA to work with initng though.

-=<( Mulperi )>=-

---

### Post by VR6Pete on 2005-10-23
Agreed, with a little tweaking it can works quite well.

I installed the smp kernel for my P4 box, installed nvidia drivers, set up prelinking . seems alot more responsive now.

---

### Post by xsence on 2005-10-23
i haven't installed nvidia drivers yet because of the problems i had installing it.

i have done:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config-enable

but nogo. nvidia logo shows but can't load glxgears.

please help me on this one

btw this is mijn xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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

Section "Extensions"
	Option 	"Composite" "Enable"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV38 [GeForce FX 5950 Ultra]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Hairy_Palms on 2005-10-23
yoir driver should be nvidia not nv
change the line   Driver "nv"
to
 Driver "nvidia"

---

### Post by xsence on 2005-10-23
[QUOTE=Hairy_Palms]yoir driver should be nvidia not nv
change the line   Driver "nv"
to
 Driver "nvidia"[/QUOTE]

that doesn;t work.. when i reboot the computer after changing nv to nvidia i get white screen twice and after that xserver crash.

That nvidia 5950ultra was my old card and have changed it to a 5700 but only have problems installing driver.

i think my system is messed up and i have to reinstall ubuntu

**UPDATE UPDATE UPDATE**

Oke guys thanks to some poeple here on this forum i have nvidia drivers fully working on my system and it changes a lot in desktop use. the only reason for windows is age of empires 3 now.. 

Ubuntu has changed a lot in my daily computing.. everything looks great now :)

---

