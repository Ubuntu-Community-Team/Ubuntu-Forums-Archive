---
title: "World of Warcraft error on wine"
date: 2007-03-07
forum: Gaming &amp; Leisure
---

### Post by alican timur on 2007-03-07
i get the error

```
Code: BadMatch error

X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 13 (X_GLXCreateGLXPixmap)
Serial number of failed request: 373
Current serial number in output stream: 374
```

just after the loading screen, and the game shuts down. I use ATI Radeon 9600, with the latest drivers installed.

here is my config.wtf:

```
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "450.000000"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET realmList "eu.logon.worldofwarcraft.com"
SET readContest "-1"
SET locale "enGB"
SET expansionMovie "0"
SET doodadAnim "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET realmName "Moonglade"
SET gameTip "21"
SET UIFaster "2"
SET gxApi "OpenGL"

```

the game runs if i delete the line 

```
SET gxApi "OpenGL"
```

but it's too slow, and i can't see myself and my character's icon on the left top corner.

and here's my Xorg.Conf:

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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "tr"
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
	Identifier   "PHILIPS 109B"
	HorizSync    30.0 - 97.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
    Driver        "fglrx"
    BusID        "PCI:2:0:0"
    Option       "UseFBDev"        "true"
    Option       "Capabilities" "0x00000800"
    Option       "UseFastTLS" "off"
    Option       "KernelModuleParm" "locked-userpages=0"

EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "PHILIPS 109B"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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

i also have low fps on games which my card should be able to run perfectly, like sauerbraten (cube 2).

i found the same error on gentoo-wiki, but it says this occurs when the user goes in a building.. my game doesn't even start..

> 
X Error of failed request: BadMatch
Note: Minimap Bug

This Is the Minimap bug, which as soon as you go into a building with it open, your game crashes

You may get an error that is similiar to this:
[QUOTE]
Code: BadMatch error

X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 13 (X_GLXCreateGLXPixmap)
Serial number of failed request: 373
Current serial number in output stream: 374[/QUOTE]

help please?

---

### Post by willskills on 2007-03-07
Argh; read the howto.

Try this, your problem looks similar;

For users with an Nvidia card who have upgraded to Wine 0.9.30 after installing, you may need to reinstall your nvidia-glx if you are crashing with the following error message when running WoW from the console:

Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 14
Current serial number in output stream: 15

/*( This can be fixed by typing: */

$ sudo apt-get install nvidia-glx

---

### Post by epennings on 2007-03-07
I have a radeon 9600 too and WoW runs fine on my pc. I notice you have some double sections in your xorg.conf. Try changing it to this:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "tr"
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
	Identifier   "PHILIPS 109B"
	HorizSync    30.0 - 97.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
    Identifier   "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
    Driver       "fglrx"
    BusID        "PCI:2:0:0"
    Option	 "VideoOverlay" "on"
    Option	 "OpenGLOverlay" "off"	
    Option       "UseFBDev"        "true"
    Option       "Capabilities" "0x00000800"
    Option       "UseFastTLS" "off"
    Option       "KernelModuleParm" "locked-userpages=0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "PHILIPS 109B"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    	"Composite" "Disable"
EndSection

Section "ServerFlags"
	Option	    	"AIGLX" "off"
EndSection
```

---

### Post by alican timur on 2007-03-07
epennings : i edited my xorg.conf as you suggested. same error.. where did you download your drivers from?

willskills : i have ATI Radeon 9600, not nVidia.

---

### Post by epennings on 2007-03-08
I installed the ati drivers using method 2 from [_this_]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") guide

I installed WoW using [_this_]("https://help.ubuntu.com/community/WorldofWarcraft") guide

---

### Post by alican timur on 2007-03-10
and can you please post your config.wts file?

---

