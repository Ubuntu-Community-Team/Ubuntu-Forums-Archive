---
title: "Feisty &amp; Beryl with dual display - running ATI x1600 ALMOST working"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by HaoTian on 2007-04-22
Hardware:
Acer Aspire 5110
AMD dual core CPU, 2ghz
2gb RAM
ATI Radeon x1600 video
15.4" 1280x800 laptop display
19" LCD panel 1280x1024 external display

After playing with this for most of the day, I managed to get xgl and beryl installed on my recent upgrade of Feisty.  It's SO close to working properly.  All of the effects work, but I dislike how my displays are being handled.

When I'm not running an XGL session, my laptop display is running at the proper 1280x800 resolution and the LCD panel is running at 1280x1024.  When I switch to an XGL session, the laptop display is stuck at the 1280x1024 resolution (so some of it is cut off on the bottom).  Also, it is now handled as a single display... when I maximize windows, they don't maximize to the single display.. they stretch across both.

Here's a copy of my Xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "pad"
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
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "GLcore"
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
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "USB" "on"
	Option	    "PressCurve" "50,0,100,50"
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "USB" "on"
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "USB" "on"
	Option	    "Mode" "relative"
EndSection

Section "InputDevice"
	Identifier  "pad"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "pad"
	Option	    "USB" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
# --- The following was added for dual-head support:
	Option	    "DesktopSetup" "horizontal"
	Option	    "PairMode" "1280x800+1280x1024" # Pair mode resolutions
	Option	    "HSync2" "79"
	Option	    "VRefresh2" "75"
	Option	    "OverlayOnCRTC2" "1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x800" "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"  #make DRI work with fglrx.
EndSection


Any suggestions on how I can get the two displays to work at their proper resolutions, like they do outside of an XGL session?  If there's any info I can provide, please let me know.

Thanks in advance!

Scott

---

