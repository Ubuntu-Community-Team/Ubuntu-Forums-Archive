---
title: "Berly problems for one user but not another..."
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by davbren on 2007-08-10
Hi, I'm having some issues. On one users account, I'm having no problems at all. Howver on another user's Beryl flat refuses to work. When I try to switch it on the screen freezes except my mouse and Ctrl+Alt+Backspace doesn't work.

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
http://www.google.co.uk/ig?hl=en
Section "Device"
	Identifier	" nVidia Corporation C51PV [GeForce 6150]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
        Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection 
```

---

### Post by dougfractal on 2007-08-10
you could add 

Option "AddARGBVisuals" "True"         # next to 
    Option "AddARGBGLXVisuals" "True"

but this is only a decoration fix.

move ~/.beryl settings
> 
cd /home/[brokenberyluser]
sudo mv .beryl beryl.broken

---

### Post by davbren on 2007-08-11
The thing is, on my mums user account I Beryl works perfectly...annoyingly so and on my account it just doesnt work, it doesnt make sense. When I try to enable Berly the whole system locks up...

---

### Post by dougfractal on 2007-08-12
> move ~/.beryl settings

did you move ~/.beryl ?  as it seems that there is a setting error in that folder.
so you can reset it by moving it.

> [ctrl+alt+f1] login as you
mv ~/.beryl beryl.old    # rename folder
[ctrl+alt+f7] login as you and your setting should be reset.


its not an xorg issue as it works for your mum.

from [http://ubuntuforums.org/showthread.php?p=1597472](http://ubuntuforums.org/showthread.php?p=1597472)
To stop beryl autostart 
> rm ~/.config/autostart/beryl-manager.desktop

---

### Post by davbren on 2007-08-14
Dude you legend it worked!! the moving of the beryl folder worked a treat thank you.

---

