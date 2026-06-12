---
title: "Issues arising from dual-screen set-up"
date: 2006-12-30
forum: Desktop Environments
---

### Post by IsenMike on 2006-12-30
Hello there.  I'm very new to linux, and I'm having some issues getting my dual-monitor setup to work.

I have an ATI Radeon X800.  I downloaded and installed the ATI drivers, and then used aticonfig to set everything up for dual screens.  This worked pretty flawlessly.  I had two independent screens, the mouse cursor moved freely between them, and I could run programs on either screen.  Unfortunately, I couldn't move windows from one screen to the other, and if an instance of a given program was running in one screen, it wouldn't start in the other (ie I couldn't have Firefox running on both screens).

I visited the IRC channel and they mentioned that I needed "xinerama," though nobody would really tell me what that was or how to use it.  A little bit of digging around online and I figured that I needed to put the line *Option "Xinerama" "true"* in my xorg.conf file.  So I did that, and now I have the dual desktop setup the way I want it, but there's a problem (isn't there always?).

When I try and change the screen resolution via System\Preferences\Screen Resolution, I get an Error message: "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

I was winging it pretty well for a while, but now I'm over my head.  What does this mean, and how can I fix it?

Here's the xorg.conf file, if it'll help:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option		"Xinerama" "true"
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
	Identifier   "NEC FE950+"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor    "NEC FE950+"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
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

---

### Post by EZ-man on 2006-12-31
Have you tryed experimentting with this for say???

and adding:

Section "ServerFlags"
     Option  "Xinerama"  "true"
EndSection

and deleting:

Option		"Xinerama" "true"

----------------------------------------------------------------------------

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Adding:    Option       "MergedFB"  "true"

-----------------------------------------------------------------------------
And whats up with that ???

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		[COLOR="Red"]Viewport   0 0[/COLOR] Delete, and add: Modes   "1280x1024"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		[COLOR="Red"]Viewport   0 0 [/COLOR]  Delete, and add: Modes  "1600X1200"
		Depth     24
	EndSubSection
EndSection



Try that...

---

### Post by EZ-man on 2006-12-31
Also, see my other link:

[http://ubuntuforums.org/showthread.php?t=328345](http://ubuntuforums.org/showthread.php?t=328345)

It will explain a bit better.

---

### Post by IsenMike on 2007-01-01
Made the changes you suggested.  Still the same error message when I try to change the resolution.  Your other link gives a pretty good explanation of what some of the xorg.conf code means, but I still don't have any idea what XRandR is, or why it's giving me this error.

---

### Post by IsenMike on 2007-01-01
Did a bit more research on my own.  According to the [Wikipedia entry on Xinerama]("http://en.wikipedia.org/wiki/Xinerama"), what I'm trying to do simply isn't possible.  I can't change resolutions on-the-fly while using Xinerama.  But by changing the Modes in the Screen sections of the xorg.conf file, I can adjust my resolution, and see the changes after restarting GNOME with CTRL-ALT-BACKSPACE.

Learning is fun.  I guess. :confused:

---

