---
title: "Can't enable desktop effects w/nVidia NV17 [GeForce4 440 Go]"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by drkyle3 on 2007-12-03
I'm new to linux and I'm just trying to activate the visual effects.
I've install the restricted drivers through the restricted driver manager.
The only thing I manually changed in the xorg file was:
------------------------------------------------------
	SubSection "Display"
		Modes		"1440x900"
------------------------------------------------------
So that I could have the correct resolution for my widescreen.

It doesn't say I need the legacy drivers for my card.
When I try to enable effects, the screen blanks and then returns with a message that it can't be activated.  Any thoughts ???

_Here's my xorg file:_

[B]# xorg.conf (xorg X Window System server configuration file)

Section "Files"
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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"nVidia Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection[/B]

---

### Post by FuturePilot on 2007-12-03
Can you post the output of 
```
compiz --replace
```

---

### Post by drkyle3 on 2007-12-04
[FONT="Arial"]kyle@Toshiba:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0174 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity[/FONT]
-------------------------------------
Do I simply need a graphics card with more memory ?

---

### Post by K.Mandla on 2007-12-04
You shouldn't. I can run Beryl at 1600x1200 on my 64Mb 440 Go. Are you sure the right driver was installed? The 100-series driver doesn't support the older Geforce cards any more; you need the 96-series driver, but I don't know if the restricted driver manager can tell if it's installing the right one.

You should be able to double-check that by running ```
glxgears -info
```(I think that's the right command :oops:) and looking for the driver entry. If it's the 100-series you might try uninstalling that driver manually and installing nvidia-glx instead.

Just an idea though.

By the way, what kind of laptop are you using? I didn't know 440s were put in widescreen laptops.

---

### Post by FuturePilot on 2007-12-04
The Compiz wrapper in Gutsy has a restriction on Nvidia cards with less that 64MB VRAM due to the black window bug. Try starting Compiz like this

```
SKIP_CHECKS=yes compiz
```
You might get black windows though.
If so, you could try running Compiz with Indirect Rendering
```
compiz --replace --loose-binding --indirect-rendering
```

---

### Post by drkyle3 on 2007-12-04
The screen on my lap top actually died.  I have it attached to a Samsung SyncMaster 932BW.

I'm not sure what I'm looking at:

kyle@Toshiba:~$ glxgears -info
GL_RENDERER   = GeForce4 440 Go/AGP/SSE2
GL_VERSION    = 1.5.8 NVIDIA 96.39
GL_VENDOR     = NVIDIA Corporation

----------------------------------------------------

kyle@Toshiba:~$ glx info
bash: glx: command not found
kyle@Toshiba:~$ glx-info
bash: glx-info: command not found
kyle@Toshiba:~$ glx info
bash: glx: command not found
kyle@Toshiba:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 440 Go/AGP/SSE2
OpenGL version string: 1.5.8 NVIDIA 96.39
OpenGL extensions:.......................

-----------------------------------------------------------------------------------------------------------

kyle@Toshiba:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0174 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaSKIP_CHECKS is yes, so continuing despite problems.
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

---

### Post by drkyle3 on 2007-12-04
I just ran the following code to install xgl per the instructions here: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Works great now.  Glad to leave Windows behind.

Thanks for all the help !

---

