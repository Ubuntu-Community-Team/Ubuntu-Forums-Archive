---
title: "changed to fglrx now mouse is weird in games!"
date: 2006-07-22
forum: Gaming &amp; Leisure
---

### Post by techrush on 2006-07-22
i was using the open source r300 (radeon) driver for my x300 card and it played quake 3 pretty well at 800x600. i decided i wanted to get more out of my card so i installed the fglrx drivers using this tutorial: [http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+mesa+install](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+mesa+install)
(i had tried the ones in the repo before unsuccessfully) 

well now i do get much better 3d performance out of my card but the mouse acts VERY strange if i put the resolution over 800x600. if i keep it at this low res it plays fine. if i put it over 800x600 the game becomes TOTALLY unplayable with very jerky mouse movements. 

i thought maybe it was a performance issue and the card really couldnt handle anything over 800x600 but im getting 90fps SOLID when in this mode. i should be able to bump up the res a little! 

i also get similar problems in ET if i put the resolution over 800x600. this is all very strange as the controls were working fine before fglrx. even when i upped the res beyond 800x600! 



anyways if anyone has any ideas whats up with this let me know :)

---

### Post by vem0m on 2006-07-22
post the contents of your /etc/X11/xorg.conf file here also do u have mouse smoothing enable in Q3?

---

### Post by techrush on 2006-07-22
here is my xorg.conf....yes i do have mouse smoothing enabled.

```
Section "ServerLayout"
	Identifier     "layout1"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Keyboard1" "CoreKeyboard"
	InputDevice    "Mouse1" "CorePointer"
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
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe" # Double-Buffering Extension
	Load  "v4l" # Video for Linux
	Load  "extmod"
	Load  "type1"
	Load  "freetype"
	Load  "drm"
	Load  "glx" # 3D layer
	Load  "dri" # direct rendering
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "kbd"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"

    # Monitor preferred modeline (59.9 Hz vsync, 55.9 kHz hsync, ratio 16/10)
	Identifier   "monitor1"
	VendorName   "Plug'n Play"
	ModelName    "LCM-19w4"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	ModeLine     "1440x900" 106.5 1440 1520 1672 1904 900 903 909 934 +hsync -vsync
	ModeLine     "1440x900_60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "device1"
	Driver      "ati"
	BoardName   "ATI Radeon"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1440 900
		Depth     8
	EndSubSection
	SubSection "Display"
		Virtual   1440 900
		Depth     15
	EndSubSection
	SubSection "Display"
		Virtual   1440 900
		Depth     16
	EndSubSection
	SubSection "Display"
		Virtual   1440 900
		Depth     24
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


```

---

### Post by vem0m on 2006-07-22
laptop or desktop?

---

### Post by Anduu on 2006-07-22
Same problems here....

To fix the problem you need to enable vsync in your games...worked like a charm for Quake3...now if I could only figure out how to enable vsync in Unreal Tournament GOTY I would be a happy man.

---

### Post by techrush on 2006-07-22
its a desktop.............how do i enable vsync ?

---

### Post by Anduu on 2006-07-22
> **techrush said:**
> its a desktop.............how do i enable vsync ?

In Quake3 it is under setup>game options>sync every frame

---

### Post by techrush on 2006-07-22
hey that did it! thanks!

---

### Post by Anduu on 2006-07-22
Cool 8) 

I think it has something to do with the fact that the mouse can't keep up when you get really high framerates...dunno :p

---

