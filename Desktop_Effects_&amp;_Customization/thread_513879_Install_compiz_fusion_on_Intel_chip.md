---
title: "Install compiz fusion on Intel chip"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by tenmoi on 2007-07-31
Dear friends,

I think I should share my experience here on installing compiz fusion. I am but a newbie but I have successfuly installed compiz fusion and is running it on my machine by following instructions on this forum. So first of all my thanks to all the "forumers"!

Second, my machine specs: Pentium 4 @ 3 GHz, 256 Meg of RAM, Intel 865G intergrated GPU. OS: Ubuntu Feisty 7.04 upgraded from Egdy. Please don't laugh at it. Compiz fusion just runs so smoothly.

Third, installation of Compiz fusion: Please follow the instructions in this link [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314). BUT BEFORE running compiz Please DO THIS: open synaptics and completely remove the i810 driver, then install the Intel graphics driver and reboot. If you have done correctly you can notice that the login name you are typing is bigger than before. Then ALT+F2 and type in "compiz --replace". Open a window and if you have not installed emerald you will not get any borders. hold down ALT and right click your mouse to drag the borderless window. If you can drag it then you know that compiz is up and running. Now what you need to do is install emerald: sudo apt-get install emerald-themes. Do a CRL+ALT+BACKSPACE to log out and in. Go to system - preferences - compiz configuration manager and tick "decorator plugin". now you ALT+F2 and type in "compiz --replace" and ALT+F2 again and type in "emerald --replace". and VOILA ! Compiz is running.

I hople this may help.:lolflag:

---

### Post by Dysan911 on 2007-08-01
This was very helpful right up to the part where you say "Install the Intel Drivers".  

What Intel Drivers?    I uninstalled the i810 but now I'm stuck in the middle here because I have no clue what your referring to when you say "Intel Drivers".    

:confused:

> **tenmoi said:**
> Dear friends,

I think I should share my experience here on installing compiz fusion. I am but a newbie but I have successfuly installed compiz fusion and is running it on my machine by following instructions on this forum. So first of all my thanks to all the "forumers"!

Second, my machine specs: Pentium 4 @ 3 GHz, 256 Meg of RAM, Intel 865G intergrated GPU. OS: Ubuntu Feisty 7.04 upgraded from Egdy. Please don't laugh at it. Compiz fusion just runs so smoothly.

Third, installation of Compiz fusion: Please follow the instructions in this link [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314). BUT BEFORE running compiz Please DO THIS: open synaptics and completely remove the i810 driver, then install the Intel graphics driver and reboot. If you have done correctly you can notice that the login name you are typing is bigger than before. Then ALT+F2 and type in "compiz --replace". Open a window and if you have not installed emerald you will not get any borders. hold down ALT and right click your mouse to drag the borderless window. If you can drag it then you know that compiz is up and running. Now what you need to do is install emerald: sudo apt-get install emerald-themes. Do a CRL+ALT+BACKSPACE to log out and in. Go to system - preferences - compiz configuration manager and tick "decorator plugin". now you ALT+F2 and type in "compiz --replace" and ALT+F2 again and type in "emerald --replace". and VOILA ! Compiz is running.

I hople this may help.:lolflag:

---

### Post by Zeezy on 2007-08-04
install **xserver-org-video-intel** in synaptic

---

### Post by vapore0n on 2007-08-09
and does everything work?

I got compiz fusion installed but most things dont work. Blur is the one I was looking forward to but it doesnt.

I had followed the same tutorial you posted, and also tried the script thats in this forum for installing CF, but that failed.

---

### Post by kurup on 2007-08-12
> **tenmoi said:**
> Dear friends,

I think I should share my experience here on installing compiz fusion. I am but a newbie but I have successfuly installed compiz fusion and is running it on my machine by following instructions on this forum. So first of all my thanks to all the "forumers"!

Second, my machine specs: Pentium 4 @ 3 GHz, 256 Meg of RAM, Intel 865G intergrated GPU. OS: Ubuntu Feisty 7.04 upgraded from Egdy. Please don't laugh at it. Compiz fusion just runs so smoothly.

Third, installation of Compiz fusion: Please follow the instructions in this link [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314). BUT BEFORE running compiz Please DO THIS: open synaptics and completely remove the i810 driver, then install the Intel graphics driver and reboot. If you have done correctly you can notice that the login name you are typing is bigger than before. Then ALT+F2 and type in "compiz --replace". Open a window and if you have not installed emerald you will not get any borders. hold down ALT and right click your mouse to drag the borderless window. If you can drag it then you know that compiz is up and running. Now what you need to do is install emerald: sudo apt-get install emerald-themes. Do a CRL+ALT+BACKSPACE to log out and in. Go to system - preferences - compiz configuration manager and tick "decorator plugin". now you ALT+F2 and type in "compiz --replace" and ALT+F2 again and type in "emerald --replace". and VOILA ! Compiz is running.

I hople this may help.:lolflag:

I too have a machine that runs on an integrated 865 graphics chip. I was thrilled to see your post as you managed to achieve running compiz-fusion on your pc. I have followed Vorian's link (the one you have mentioned at the top)  to the T; it installed allfine..but throws an error on starting compiz.

rajesh@kurup:~$ compiz --replace -c emerald &
[1] 6560
rajesh@kurup:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -c


Am posting my xorg.conf if that could be of any help:


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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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



Also here's the output of my xgl:

rajesh@kurup:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Have been scratching my head all day long but to no avail. Can I get a pointer to where am going wrong?

---

### Post by DarkN00b on 2007-08-12
Compiz Fusion works great on my laptop using the i810 driver...

'Course I'm running with 768 megs of ram.

---

