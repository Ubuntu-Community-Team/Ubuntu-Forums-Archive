---
title: "GDM starts on wrong monitor"
date: 2008-06-24
forum: Desktop Environments
---

### Post by ghostmac on 2008-06-24
After a reboot, GDM starts on my accessory monitory rather than my main display. 
Could someone shed some insight as to where GDM looks to find out which display it shows on?

---

### Post by Zorael on 2008-06-24
Please post your **/etc/X11/xorg.conf** file.

---

### Post by ghostmac on 2008-06-24
```
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection
Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1920x1200"
    HorizSync       31.5 - 74.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "@@@ L7AK2"
    HorizSync       31.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection
Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1600x1200@60" "1400x1050@60" "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1024x768@60 +1600+0, DFP: 1600x1200@60 +0+0; CRT: NULL, DFP: 1400x1050@60 +0+0; CRT: NULL, DFP: 1280x1024@60 +0+0; CRT: NULL, DFP: 1280x960@60 +0+0; CRT: NULL, DFP: 1024x768@60 +0+0; CRT: NULL, DFP: 800x600@60 +0+0; CRT: NULL, DFP: 800x600@56 +0+0; CRT: NULL, DFP: 640x480@60 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1920+0, DFP: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1920x1200 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1920+176, DFP: 1920x1200 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1920+176, DFP: 1920x1200 +0+0; CRT: nvidia-auto-select +320+176, DFP: 1920x1200 +0+0"
EndSection

```

---

### Post by Zorael on 2008-06-25
That is one messy xorg.conf. :> I imagine you're running Gutsy or earlier, or at the very least, upgraded to Hardy? Hardy (and later) xorgs are much slimmer, less things explicitly defined, more stuff getting autodetected. But no need to shave things off of it if it works, I guess.

Anyway, try replacing the contents with this. Again, **/etc/X11/xorg.conf**.
```
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "ServerFlags"
	Option		"Xinerama" "0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc105"
	Option		"XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ImPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	VendorName	"Generic LCD Display"
	ModelName	"LCD Panel 1920x1200"
	HorizSync	31.5 - 74.5
	VertRefresh	56.0 - 65.0
	Gamma		1
	ModeLine	"640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine	"800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine	"800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine	"1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine	"1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine	"1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine	"1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine	"1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Unknown"
	ModelName	"@@@ L7AK2"
	HorizSync	31.0 - 80.0
	VertRefresh	50.0 - 75.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	BoardName	"nv"
	Screen		0
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce 8600 GT"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection	"Display"
		Virtual	1600 1200		# Remove this line if the login screen gets "too big"
		Depth	24
		Modes	"1600x1200@60" "1400x1050@60" "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option		"TwinView" "1"
	Option		"metamodes" "CRT: nvidia-auto-select +1920+176, DFP: 1920x1200 +0+0; CRT: nvidia-auto-select +320+176, DFP: 1920x1200 +0+0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 **"Default Screen"** 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```
The only important change is in the ServerLayout section; replacing "Screen0" with "Default Screen".

---

### Post by ghostmac on 2008-06-25
So I replaced "Screen0" with "Default Screen"and gnome started up in low res mode and my accessory monitor (@@@ L7AK2) didn't turn on, though gdm did start on the correct display (LCD Panel 1920x1200).
May I have missed something or do I need to make this change and re-run nvidia-settings?

---

