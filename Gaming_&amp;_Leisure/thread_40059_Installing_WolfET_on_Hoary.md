---
title: "Installing WolfET on Hoary?"
date: 2005-06-07
forum: Gaming &amp; Leisure
---

### Post by Caffeine on 2005-06-07
I'm still new to Ubuntu, and this forum has been a great help so far, and I thank you all for it.  But, to the point, here's today's "annoying newbie question"...

I'm a WolfET addict, and I've been without since I converted.  I have what I believe to be the correct archive from SplashDamage's site, et-linux-2.60.x86.run , and from there, I'm fairly unsure as of how to install it properly, without taking potshots and possibly screwing up my system.

Thanks beforehand to all that can help out here.

---

### Post by dolny on 2005-06-07
Just do it from console:

```
./et-linux-2.60.x86.run
```

Then the installer will launch and you will choose the path etc. Very easy. You will know what to do. Install it somewhere to /home/yournick/games/et/ or something.

---

### Post by Caffeine on 2005-06-07
Tried that in console, and I'm getting a permission denied error.  Tried with sudo and from root, all denied.

---

### Post by Gtaylor on 2005-06-07
Try this:
> 
sudo chmod a+x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run

Assuming you want to install it into /opt and make it publicly available, otherwise leave the sudo's out and install it under your home directory.

---

### Post by Caffeine on 2005-06-07
Thanks for the quick help.  Got the game installed without a problem now, and it's running more smoothly than I've ever seen it on this system.  Guess having no Windows junk bogging the system down gave a real kickstart to it.

---

### Post by Gtaylor on 2005-06-07
Yeah, I've found it to run very well on my box as well as opposed to Windows. Glad to hear it worked out for you, happy gaming!

---

### Post by fireedo on 2005-06-12
[QUOTE=Gtaylor]Yeah, I've found it to run very well on my box as well as opposed to Windows. Glad to hear it worked out for you, happy gaming![/QUOTE]
 how to uninstall wolfenstein?

---

### Post by Gtaylor on 2005-06-12
Delete the folder where you installed it.

---

### Post by fireedo on 2005-06-12
[QUOTE=Gtaylor]Delete the folder where you installed it.[/QUOTE]
 just delete?.....not with uninstall or something?....alright then....thanx anyway :)

---

### Post by fireedo on 2005-06-12
damn still not getting work.....just blank screen.....

---

### Post by fireedo on 2005-06-12
[QUOTE=fireedo]damn still not getting work.....just blank screen.....[/QUOTE]
 hikmah@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/hikmah/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...
hikmah@ubuntu:~$

---

### Post by fireedo on 2005-06-12
and if I use  ------>If this is intentional, add
"+set r_allowSoftwareGL 1"

 hikmah@ubuntu:/usr/local/games/enemy-territory$ et +set r_allowSoftwareGL 1
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/hikmah/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect
...using software Mesa (r_allowSoftwareGL==1).
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_VERSION: 1.2 (1.5 Mesa 6.2.1)
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(16-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...
hikmah@ubuntu:/usr/local/games/enemy-territory$

I shutdown with hit "ctrl+c"....because it show me just blank screen

---

### Post by fireedo on 2005-06-12
[QUOTE=fireedo]and if I use  ------>If this is intentional, add
"+set r_allowSoftwareGL 1"

 hikmah@ubuntu:/usr/local/games/enemy-territory$ et +set r_allowSoftwareGL 1
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/hikmah/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect
...using software Mesa (r_allowSoftwareGL==1).
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_VERSION: 1.2 (1.5 Mesa 6.2.1)
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(16-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...
hikmah@ubuntu:/usr/local/games/enemy-territory$

I shutdown with hit "ctrl+c"....because it show me just blank screen[/QUOTE]
 and if this help this is my xorg.conf :

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
        Option "backingstore" "true"
        Option "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Gtaylor on 2005-06-12
[QUOTE=fireedo]damn still not getting work.....just blank screen.....[/QUOTE]
What do you mean? You're trying to uninstall it but it's not working and you post your xorg? Are you trying to get it working or are you trying to get rid of it?

---

### Post by fireedo on 2005-06-12
[QUOTE=Gtaylor]What do you mean? You're trying to uninstall it but it's not working and you post your xorg? Are you trying to get it working or are you trying to get rid of it?[/QUOTE]
 I unistall it because I want to reinstall....and still not getting work

---

### Post by fireedo on 2005-06-12
[QUOTE=fireedo]I unistall it because I want to reinstall....and still not getting work[/QUOTE]
 at last!!!...it's work.....i found it the problem....that I must turn off "sound server".........thats it...but now I have a new problem....there is no sound on my wolfenstein:ET....so can anyone help me,please....thanx :)

---

