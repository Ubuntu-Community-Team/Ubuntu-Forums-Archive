---
title: "WoW Issues"
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by trxDraxon on 2007-02-20
I was wondering if anyone has anymore suggestions on anything I can try to get better FPS running WoW under Wine on Edgy.  Like most other posts I've read through I get 30ish FPS indoors but the minute I step out doors it drops to 10 and in Outlands its even worse.

I have done the REG tweak, added opengl to my config.wtf file and direct rending is running.  I am nto sure really what to try next.  Everything else on my system is running very smoothly and they way I want it(minus the beryl update this morning but thats another thread ;P).  Here is some info on my machine:

Dell XPS Laptop
P4 3.4ghz HT
1gig of ram
ATI Mobility 9700
Ubuntu Edgy fully patched
FLGRX drivers loaded using Envy


```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

```
glxinfo | grep rendering
direct rendering: Yes
```

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Load  "dbe"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1200"
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
	Option	    "Composite" "Disable"
EndSection
```


```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET farclip "477"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET baseMip "1"
SET movie "0"
SET expansionMovie "0"
SET mouseSpeed "1"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET profanityFilter "0"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET realmList "us.logon.worldofwarcraft.com"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraDistanceMaxFactor "3.5"
SET realmName "Darkspear"
SET gameTip "64"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET minimapInsideZoom "0"
SET uiScale "1"
SET autoSelfCast "1"
SET scriptMemory "66560"
SET minimapZoom "0"
SET readScanning "-1"
SET readContest "-1"
SET checkAddonVersion "0"
SET accountName "censored"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET shadowLevel "0"
SET lastCharacterIndex "1"
```

---

