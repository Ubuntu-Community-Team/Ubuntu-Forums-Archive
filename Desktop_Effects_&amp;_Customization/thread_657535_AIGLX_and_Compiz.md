---
title: "AIGLX and Compiz"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by Lumby on 2008-01-03
I recently decided to give ATI's proprietary drivers a run for its money to see if it might work out better with my FireGL 5200. XGL/Mesa/Compiz works perfectly for me, however I am attempting to get fglrx/AIGLX/Compiz to work and having great difficulty.

After following the detailed directions at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) my ATI drivers are successfully installed.

```

matthew@matthew-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200
OpenGL version string: 2.1.7170 FireGL Release

```

After that I checked my xorg.conf file to make sure that the composite extension is enabled

```


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	Option		"AIGLX"	"True"
	Option		"IgnoreABI"	"on"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option		"UseFastTLS"	"2"
	Option		"RenderAccel"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"(pitch"	"1600)"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"DAMAGE"	"true"
	Option		"RENDER"	"true"
	Option		"Composite"	"Enable"
EndSection


```

All appears to be valid, but yet when I try to run compiz fusion I get this message.

```

matthew@matthew-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c4 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7470): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension

```

I am at a loss for where to go, the composite extension is clearly enabled yet compiz continues to say that it is not. Any help would be appreciated.

---

