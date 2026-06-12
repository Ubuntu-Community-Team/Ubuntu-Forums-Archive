---
title: "issues expanding video across 3 monitors"
date: 2006-08-28
forum: Desktop Environments
---

### Post by bartmanbsd on 2006-08-28
Hello all,

I am running the latest version of Ubuntu with two Nvidia cards using the SLI connector to combind them.  I was able to get xorg working and span across all three monitors with the proper refresh rate.  However, when I want to play a video full screen it only covers a little over two monitors.  It seems to stop where the panel stops.  Is there a way to hack to the panel to have it expand to the end of the third screen or do I need to change something in my xorg file?  Bellow is the contents of my xorg file.  Thanks in advance for the help!

Cheers,

JD

# xorg.conf (xorg X Window System server configuration file)
# Layout with Xinerama
# ----- First Quadro, Dual Screen in Twinview ----
# ----- Second Card, Thirds Monitor in Xinerama -----

Section "ServerLayout"
	Identifier     "DIVE Twinview plus Xinerama"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" 2240 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "DevInputMice" "AlwaysCore"
EndSection

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
#	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "Xinerama"
EndSection

Section "InputDevice"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#	Option	"Xleds"		"1 2 3"
# To disable the XKEYBOARD extension, uncomment XkbDisable.
#	Option	"XkbDisable"
# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#	Option	"XkbModel"	"pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#	Option	"XkbModel"	"microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#	Option	"XkbLayout"	"de"
# or:
#	Option	"XkbLayout"	"de"
#	Option	"XkbVariant"	"nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#	Option	"XkbOptions"	"ctrl:swapcaps"
# Or if you just want both to be control, use:
#	Option	"XkbOptions"	"ctrl:nocaps"
#
	Identifier  "Keyboard0"
	Driver      "keyboard"
	Option	    "XkbRules" "xfree86"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "InputDevice"

# If the normal CorePointer mouse is not a USB mouse then
# this input device can be used in AlwaysCore mode to let you
# also use USB mice at the same time.
	Identifier  "DevInputMice"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "no"
EndSection

Section "Monitor"

	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "0"
	HorizSync    31.5 - 150.0
	VertRefresh  50.0 - 100.0
	ModeLine     "1280x1024_60" 105.8 1280 1320 1440 1680 1024 1026 1030 1050
	Option	     "dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "0"
	HorizSync    31.5 - 150.0
	VertRefresh  50.0 - 100.0
	ModeLine     "1280x1024_60" 105.8 1280 1320 1440 1680 1024 1026 1030 1050
	Option	     "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "Nvidia"
	BoardName   "Quadro FX4400"
	Option	    "TwinView"
	Option	    "SecondMonitorHorizSync" "31.5-150"
	Option	    "SecondMonitorVertRefresh" "50-100"

	Option	    "MetaModes" "1280x1024_60 +0+0,1280x1024_60 +1120+0"

	Option	    "ConnectedMonitor" "crt,crt"
#	Screen0
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "nvidia"
	VendorName  "Nvidia"
	BoardName   "Second Quadro FX4400"

	Option      "MetaModes" "1280x1024_60"

	# Screen1
	BusID       "PCI:129:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	        Modes    "1280x1024_60"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024_60"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

---

### Post by bartmanbsd on 2006-08-30
This became fixed when I installed all the "eye candy" stuff from the [http://ubuntuguide.org/wiki/Dapper#Eye_Candy](http://ubuntuguide.org/wiki/Dapper#Eye_Candy)  website.....

---

