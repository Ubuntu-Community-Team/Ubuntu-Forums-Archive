---
title: "Problem with kubuntu in edgy: module Display could not be loaded in System Settings"
date: 2007-01-05
forum: Desktop Environments
---

### Post by Zebedee66 on 2007-01-05
suddenly i cannot load the display module from the kde system settings anymore:

heres what i get running  "$kcmshell displayconfig":

[FONT="Courier New"]Pythonize constructor -- pid = 5858
Python interpreter initialized!



Pythonize constructor -- pid = 5858
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.4/displayconfig.py", line 1685, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.4/displayconfig.py", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 321, in __init__
    if bus_id == self._canonicalPCIBusID(device_section.busid):
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 527, in _canonicalPCIBusID
    parts = bus_id.split(":")
AttributeError: 'NoneType' object has no attribute 'split'
error: *** runFunction failure
;
[/FONT]

This is my xorg.conf:

[FONT="Courier New"]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
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
	Option	    "XkbLayout" "de"
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

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "stylus"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "eraser"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "eraser"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "cursor"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "cursor"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"

        # V-freq: 60.00 Hz  // h-freq: 63.73 KHz
	Identifier   "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	ModeLine     "1280x1024" 109.6 1280 1336 1472 1720 1024 1024 1026 1062
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
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
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
[/FONT]

I've been running an ati radeon with the fglrx drivers and didn't have this problem before. Also i've tried re-installing kde-guidance, but this didn't do anything.

Anybody got an idea?

---

