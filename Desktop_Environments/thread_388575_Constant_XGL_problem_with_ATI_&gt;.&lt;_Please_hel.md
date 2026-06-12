---
title: "Constant XGL problem with ATI &gt;.&lt; Please help."
date: 2007-03-19
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2007-03-19
Ive tried many things to get composite window managers to work on my system. Here are some specs:

Ati Radeon X1600pro AGP 8x
XGL/Compiz both from the Ubuntu 6.06 Repositories 
Ati proprietary fglrx drivers

Heres my xorg.conf file:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
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

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "F-417"
	HorizSync    24.0 - 80.0
	VertRefresh  49.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "XaaNoOffscreenPixmaps"
	Option	    "UseFastTLS" "off"
	Option	    "TexturedVideoSync" "on"
	Option	    "Capabilities" "0x00000000"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "PseudoColorVisuals" "on"
	Option	    "Centermode" "full"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "KernelModuleParm" "locked-userpages=0"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "F-417"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

Heres the output for fglrxinfo as far as running the normal Xorg 7.0 xserver. **Ill post the xgl output once I restart in xgl:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)

```

and I have direct rendering except in XGL of course. 

My problem is that whenever I enable a composite window manager (ive done beryl and compiz in dapper and edgy, all inwhich failed) my window borders dissapear. This really has me pissed :mad: :lolflag:  Is there something that I must do to fix the problem? At the momment I have compiz installed and dont really plan on using beryl unless I must. Please, any information will be appreciated :) If needed Ill try and get some screenies up :P so please sit tight

***EDIT*** Ok I tried going into XGL to get back on the forums to post the exact output of 'fglrxinfo'. Well its soo slow in XGL when I type in a URL in firefox it does like 1 character every 4 seconds... SO LAGGY. But, I know that the output is different (says mesa) but it also says something about a missing xfree86 thing on display 0.0... whatever that means.

Heres the screen
[IMG]http://i59.photobucket.com/albums/g319/b1z3rker/Screenshot.png[/IMG]

---

### Post by WalmartSniperLX on 2007-03-19
oops I guess this should have been in the video forum maybe ? :mad: ... and guess no one knows what the problem is. Darn. Well im getting a new pc ordered tomorrow so ill no longer have to put up with this POS X1600pro... it really sucks in linux.

---

