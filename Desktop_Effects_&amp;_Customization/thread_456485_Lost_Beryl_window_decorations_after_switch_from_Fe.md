---
title: "Lost Beryl window decorations after switch from Feisty to Ubuntu Studio"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by DJ_Peng on 2007-05-27
I had Beryl working fie with Ubuntu Feisty on my Nvidia GeForce2 MX400 (which for some reason is reporting as a GeForce MX100), but when I switched to Ubuntu Studio Beryl hangs up and I can't get the window decorations to work. When I ran Beryl from the terminal this is what I got
> peng@IceBox:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
beryl: pixmap 0x2e000de can't be bound to texture
beryl: Couldn't bind redirected window 0x1202768 to texture
beryl: pixmap 0x2e000e4 can't be bound to texture
beryl: Couldn't bind redirected window 0x12026bd to texture
X connection to :0.0 broken (explicit kill or server shutdown).At which point I killed Beryl. Any ideas what I can try to get Beryl to work under Studio? Here's my xorg.conf> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Nvidia GeForce MX100"
	Driver		"nvidia"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce MX100"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option         "Composite"	"Enable"
EndSection

---

