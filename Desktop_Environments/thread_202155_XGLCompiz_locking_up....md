---
title: "XGL/Compiz locking up..."
date: 2006-06-22
forum: Desktop Environments
---

### Post by nickoli_02 on 2006-06-22
Hey, I followed the howto on how to fix the lockups with ATI x-series cards here: [HTML]http://ubuntuforums.org/showthread.php?t=150854[/HTML] and inserted the code into my xorg.conf file, and it didn't fix the lockup issue. Here's my xorg.conf file...

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
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "vesa"
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
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
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

#for XGL/Compiz...
Section "Device"
   Identifier  "card0"
   Driver      "fglrx"
   Option       "no_accel" "no"
   Option       "no_dri" "no"
   Option       "DynamicClocks" "on"
   Option       "mtrr" "on"
   Option       "DesktopSetup" "Single"
   Option       "ScreenOverlap" "0"
   Option       "Capabilities" "0x00000000"
   Option       "CapabilitiesEx" "0x00000000"
   Option       "VideoOverlay" "on"
   Option       "OpenGLOverlay" "off"
   Option       "CenterMode" "off"
   Option       "PseudoColorVisuals" "off"
   Option       "Stereo" "off"
   Option       "StereoSyncEnable" "1"
   Option       "FSAAEnable" "no"
   Option       "FSAAScale" "1"
   Option       "FSAADisableGamma" "no"
   Option       "FSAACustomizeMSPos" "no"
   Option       "FSAAMSPosX0" "0.000000"
   Option       "FSAAMSPosY0" "0.000000"
   Option       "FSAAMSPosX1" "0.000000"
   Option       "FSAAMSPosY1" "0.000000"
   Option       "FSAAMSPosX2" "0.000000"
   Option       "FSAAMSPosY2" "0.000000"
   Option       "FSAAMSPosX3" "0.000000"
   Option       "FSAAMSPosY3" "0.000000"
   Option       "FSAAMSPosX4" "0.000000"
   Option       "FSAAMSPosY4" "0.000000"
   Option       "FSAAMSPosX5" "0.000000"
   Option       "FSAAMSPosY5" "0.000000"
   Option       "UseFastTLS" "0"
   Option       "BlockSignalsOnLock" "on"
   Option       "UseInternalAGPGART" "no"
   Option       "ForceGenericCPU" "no"
   Option       "KernelModuleParm" "agplock=0"
   Option       "PowerState" "1"
   BusID       "PCI:1:0:0"
EndSection

```

Any ideas? Thanks guys :)

---

### Post by nickoli_02 on 2006-06-24
hate to do this, but...

bump

---

