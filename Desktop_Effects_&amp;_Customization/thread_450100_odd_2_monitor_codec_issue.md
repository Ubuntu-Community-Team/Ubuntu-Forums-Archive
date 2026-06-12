---
title: "odd 2 monitor codec issue"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by EBo on 2007-05-21
I have recently installed feisty after being a long time FreeBSD and Fedora user. Thus far, I love it! I am, however, having an odd issue. 

I have an HP Pavilion dv5000 with a nVidia GeForce Go 7400. I have set up the s-video out to work as a second desktop on my TV. I am able to move my mouse between the desktops, but not windows and this is as I want it. My issue is this:

1. Start X, get both desktops, make popcorn, etc....
2. Open Movie Player (or any other Video player) on the TV.
3. Browse to and open the desired video.
4. Get error that proper codec cant be found
5. Leave same movie player instance open on TV, then browse to file on the laptop display, right click and "Open with 'Movie Player'"
6. File plays properly in the Movie Player instance on the TV. 

Basically I have to open the Movie player on the TV then open the file on the laptop display. Whats going on, and anyone know how this could be fixed?

EDIT - Further research!

I have found that I only get the "there is no input plugin to handle the location of this movie" error when trying to open a file stored elsewhere on the network. If I open a file of the same type locally it works fine. But if I open that same file through the network on screen 0 it plays on screen 1

I have played with the xorg.conf. The edits have improved the appearance of the images but not changed the function or affected the above error.

xorg.conf as follows:

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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

Section "Device"


    Identifier     "NvidiaOut1"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"


    Identifier     "NvidiaOut2"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung"
    ModelName      "Unknown"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NvidiaOut1"
	Monitor		"Monitor0"
	DefaultDepth	24
    Option         "NoPowerConnectorCheck" "true"
    Option         "NvAgp" "1"
    Option         "NoLogo" "1"
    #Option         "UseDisplayDevice" "CRT-0"
    Option         "RenderAccel" "true"
    Option         "UseEdidDpi" "FALSE"
    Option         "DPI" "96 x 96"
    Option         "AllowGLXWithComposite"
    Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"

   #Option     "NoPowerConnectorCheck" "true"
    Identifier     "Screen1"
    Device         "NvidiaOut2"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "NvAgp" "1"
    Option         "NoLogo" "1"
    Option         "UseDisplayDevice" "CRT-1"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "UseEdidDpi" "FALSE"
    Option         "DPI" "86 x 86"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

