---
title: "ATI + Beryl"
date: 2007-03-19
forum: Desktop Environments
---

### Post by progrockusa on 2007-03-19
ok heres the issue i have. i have an ATI mobility 9700
```
prog@prog-laptop:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```
this is what i get when i try to activate beryl please help ty

---

### Post by WalmartSniperLX on 2007-03-20
Are you running AIGLX? AIGLX should work with your card using the opensource drivers "ati"


==For AIGLX==
Make sure this is at the end of your xorg.conf file if you wish to work with AIGLX (requires xorg 7.1 or Edgy ; dapper doesnt have AIGLX in it out of the box)

```
 
gksudo gedit /etc/X11/xorg.conf

```

Add or edit on the bottom of the file:

```

Section "Extensions"
        Option      "Composite" "Enable"
EndSection

```

and make sure under the Device section, that you have 'ati' as your driver, not fglrx.

Then hit Ctrl+Alt+Backspace to restart the xserver, and log back in.

(Please include more information when asking for help by stating your current driver, what session you're running, etc so we can help you easier)

---

### Post by progrockusa on 2007-03-20
i'm set to xgl it's enabled.
still don't get the beryl splash and nothing seems to have changed.
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
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
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
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
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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
	Option	    "Composite" "Enable"
EndSection

Section "Extensions"
  Option "Composite" "0" 
EndSection
```

---

### Post by WalmartSniperLX on 2007-03-20
Please read everything before executing anything 

First of all, you need to remove what I told you to add before since you already have it there. Sorry, I didnt know. Then where it says below that:

```

Section "Extensions"
  Option "Composite" "0" 
EndSection

```
Change the "0" to "1"

Then try this:

```
 
beryl-manager

``` 

If you have beryl-manager installed it should show a red gem icon up by your clock. Right click that and select beryl as your window manager. If you dont have beryl-manager, try this:

```

beryl --replace

```
_____________________________________________________________________________________________________________________________________________________

IF THAT DOESNT HELP, DO THIS: 

By the looks of it you have 2 device sections which is generated by default and not really necesary. And, judging by your terminal output, you are running AIGLX, not XGL. XGL is a different session/xserver and its a hassle. Because of that, do the following:

```

sudo dpkg-reconfigure xserver-xorg

``` 

Then when it asks for what driver to use, make sure you go down the list and select '**ati**'. I would recommend selecting '**ati**' since fglrx wont work with composite rendering. From there after just click yes on the defaults (dont change anything). Then restart the xserver : ctrl+alt+backspace


After that, after logging in, if beryl doesnt load, load beryl-manager again with the command 'beryl-manager'. Then select beryl as your window manager by right clicking the red ruby icon. (again if you dont have beryl manager, try beryl --replace)

---

