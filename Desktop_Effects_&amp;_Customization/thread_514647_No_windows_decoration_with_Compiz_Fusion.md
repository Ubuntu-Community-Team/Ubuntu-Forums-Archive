---
title: "No windows decoration with Compiz Fusion"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by FreakTech on 2007-08-01
I just installed Compiz fusion and everything went well until I activated it.  When I did my window decorations disappeared.  Here is the shell output when I ran compiz --replace.  At the end is the problem, but I have no idea how to fix it.  Any help would be greatly appriciated.

  ```
cmuncy@HPLAP:~$ compiz --replace
Backend     : gconfAdding plugin fs (fs) 
Integration : true
Profile     : default
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin cubereflex (cubereflex)
Adding plugin ezoom (ezoom)
Adding plugin ring (ring)
Adding plugin blur (blur)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin move (move)
Adding plugin imgjpeg (imgjpeg)
Adding plugin resize (resize)
Adding plugin dbus (dbus)
Adding plugin png (png)
Adding plugin vpswitch (vpswitch)
Adding plugin switcher (switcher)
Adding plugin annotate (annotate)
Adding plugin mblur (mblur)
Adding plugin gotovp (gotovp)
Adding plugin fade (fade)
Adding plugin showdesktop (showdesktop)
Adding plugin gears (gears)
Adding plugin opacify (opacify)
Adding plugin snap (snap)
Adding plugin scalefilter (scalefilter)
Adding plugin bench (bench)
Adding plugin water (water)
Adding plugin trailfocus (trailfocus)
Adding plugin clone (clone)
Adding plugin expo (expo)
Adding plugin splash (splash)
Adding plugin decoration (decoration)
Adding plugin plane (plane)
Adding plugin put (put)
Adding plugin inotify (inotify)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin zoom (zoom)
Adding plugin wall (wall)
Adding plugin firepaint (firepaint)
Adding plugin resizeinfo (resizeinfo)
Adding plugin cube (cube)
Adding plugin scaleaddon (scaleaddon)
Adding plugin glib (glib)
Adding plugin rotate (rotate)
Adding plugin crashhandler (crashhandler)
Adding plugin regex (regex)
Adding plugin reflex (reflex)
Adding plugin fadedesktop (fadedesktop)
Adding plugin svg (svg)
Adding plugin winrules (winrules)
Adding plugin thumbnail (thumbnail)
Adding plugin workarounds (workarounds)
Adding plugin place (place)
Adding plugin wobbly (wobbly)
Adding plugin group (group)
Adding plugin neg (neg)
Adding plugin animation (animation)
Adding plugin video (video)
Adding plugin minimize (minimize)
Adding plugin extrawm (extrawm)
Initializing core options...done
Initializing move options...done
Initializing resize options...done
/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

Initializing decoration options...done
Initializing zoom options...done
Initializing workarounds options...done
Initializing place options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing minimize options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done
/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

```

---

### Post by Waappu on 2007-08-01
Hi

Could you post your xorg.conf?

---

### Post by FreakTech on 2007-08-01
sorry it took so long here you go ```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [GeForce Go 7400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [GeForce Go 7400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Waappu on 2007-08-01
Hi

Remove these lines from xorg.conf
```
Section "DRI"
	Mode	0666
EndSection
```

and add these lines```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by arbulus on 2007-08-01
Be sure you have Emerald installed

```
sudo apt-get install emerald*
```

When you're ready to run Compiz Fusion, in the terminal type:

```
compiz --replace -c emerald &
```

That worked for me.  Then you can change your Emerald theme under System>Preferences>Emerald Theme Manager

---

### Post by Likenota on 2007-12-05
that doesnt work... compiz --replace -c emerald &  i dont know what you people are doing to think that works but it doesnt..

---

