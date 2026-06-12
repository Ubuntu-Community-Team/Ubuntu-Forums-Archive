---
title: "[XGL/Beryl/ATI] Video diagonal lag/flicker/vsync problem"
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by owhno on 2007-03-15
Well i have got a serious irritating issue. 
Ati/xgl/beryl works great everything works. But it has a vsync error i think and i have tried to tweak the refresh rate / vblank options but nothing helps.

recordMyDesktop was not quick enough to record it so here a video capture with a camera:

[<YouTube>]("http://www.youtube.com/watch?v=cJ0rKJxKn10")
(Dont mind the insane flipping was holding ctrl+alt+left :P)

This is the last error in xgl/beryl i need to fix then everything works great.

System:

Ubuntu edgy 6.10
ATI 8.34.8 (x200m)
MSI S271 (AMD64 TL50 X2)
Beryl: 0.2.0

fglrxinfo (nothing wierd):
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
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
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Capabilities" "0x00000800"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
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
	Option	    "Composite" "0"
EndSection
```

---

### Post by ghstzr0 on 2007-07-15
You know, I'm having this same problem...  It seems that no one knows the answer.  :(

---

### Post by mfolnovic on 2007-07-15
This is fglrx 2 years old bug!

---

### Post by mfolnovic on 2007-07-15
hmm, try this:
aticonfig --enable-monitor=lvds,crt1
this remove flickering, but on compiz, my ubuntu slows down !!! :(

---

### Post by owhno on 2007-07-18
Sorry doesnt help.. my laptop doesnt have tvout only vga so aticonfig crashes and deletes my xorg.conf

Any other ideas?

---

### Post by benbooth on 2007-07-18
To me your xorg.conf file looks incorrect.

Although you have **fglrx** installed...it's not actually running. You're using the **ati** driver.

Try changing:

[FONT="Courier New"]Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

to...

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection[/FONT]

this should at least get get you using FGLRX.

Ben

---

