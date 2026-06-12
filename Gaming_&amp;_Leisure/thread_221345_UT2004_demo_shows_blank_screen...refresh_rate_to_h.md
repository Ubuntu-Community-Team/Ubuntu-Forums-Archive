---
title: "UT2004 demo shows blank screen...refresh rate to high"
date: 2006-07-23
forum: Gaming &amp; Leisure
---

### Post by techrush on 2006-07-23
i downlaoded and installed the ut2004 demo the install went fine but when i try to launch the game the screen just goes blank and my monitor gives me a message "OUT OF RANGE" in bright red. 

i was getting this same error before i had xorg configured correctly. it had to do with my video card sending out a signal at too high a refresh rate for my LCD. needless to say im not happy to see this error reappear! 

my setup is a pentium D w/1gb ram and a ati x300. here is my xorg.conf:

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



please help :)

---

### Post by _simon_ on 2006-07-23
I don't think UT2004 supports 1440x900, I may be wrong though.

I think you need to add some more resolutions to your xorg.

Mine looks like this, my highest res is 1280x1024:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by techrush on 2006-07-23
i added a 1024x768 mode to my xorg.conf but no luck. i did get further though. the game ran in a window for about 20 seconds then switch my whole screen black again and left me with the same OUT OF RANGE error message.

---

### Post by _simon_ on 2006-07-23
Is this a fresh install of UT2004? If so I believe it runs at 800x600 as default... try adding that, hopefully you can get in properly then and change the res to suit!

---

### Post by techrush on 2006-07-23
tried adding the 800x600 to modes also. still get the same problem. btw i get the same problem tryign to run the postal 2 demo although quake 3 and ET run great.

---

