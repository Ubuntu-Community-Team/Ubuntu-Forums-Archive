---
title: "Doom3 error newbie"
date: 2005-09-19
forum: Gaming &amp; Leisure
---

### Post by jjbennee on 2005-09-19
I get this error when I try to run Doom 3 demo... can someone help a newbie like me?


DOOM 1.1.1286 linux-x86 Nov 28 2004 20:09:31
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
Alias: ubuntu
local IP: 127.0.0.1
local IP: 192.168.0.89
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3-demo/demo/demo00.pk4 with checksum 0xfe75bbef
Current search path:
/home/cobra/.doom3-demo/demo
/usr/local/games/doom3-demo/demo
/usr/local/games/doom3-demo/demo/demo00.pk4 (12234 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
/proc/cpuinfo CPU frequency: 1978.18 MHz
guessing video ram ( use +set sys_videoRam to force ) ..
Setup X display connection
guess failed, return default low-end VRAM setting ( 64MB VRAM )
Detected
        1.98 GHz CPU
        512 MB of System memory
        64 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_texture_mirror_once GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.9
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 15052 frames ( 60208 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()


We looked at the threads and found similar problems.  We tried to configure the xorg.conf file, but we don't know what or how to edit it.

We included the xorg.conf file below if it helps:

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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


Thanks for any help on this!!!

---

### Post by jjbennee on 2005-10-03
Ok... nobody helped me here, but through lots and lots of research I figured out how to fix the problem.  BTW I have a nvidia 5900 ultra card
Make sure you can get into "su" at the terminal.  To do this goto: System->Administration->Users and Groups
check "show all users and groups"
click on "root" then go to properties (on right hand side)
set the password
Click ok
Now open a terminal window
type "su"
enter your password you made for root
now type
"gedit /etc/X11/xorg.conf"
Go down to the area where it says
**Driver "nv"**
(or Driver "vesa")
replace with
**Driver "nvidia"**
In the Module section, make sure you have:
**Load "glx"**
You should also put a "#" behind the following lines or you can delete them:
[B]Load "dri"
Load "GLcore"[/B]
Save the file
reboot the computer or if you know what your doing restart X
go into the terminal again and type:
doom3
or
doom3-demo
It should work... however now my sound is all technoee and garbled.  Does anyone have a fix for this?

---

### Post by seethru on 2005-10-03
you could have skipped all of that by using sudo...

sudo gedit /etc/X11/xorg.conf, so anyone reading this it's best not to enable root and just use sudo.

---

### Post by jjbennee on 2005-10-04
Ok once again nobody helped me with my sound problem but this one wasn't as painful to fix as the openGL errors.  It appears that Ubuntu made some errors with the ALSA configuration so what I did was force doom3-demo to use the oss emulation.  If any of you have problems with your sound in doom3 or doom3-demo start the game with this command:

**doom3-demo +set s_driver oss**
or
**doom3 +set s_driver oss**

To make this permanent, I still don't know.  Does anyone else have a solution?

---

### Post by seethru on 2005-10-04
try running the game with oss emulation through alsa.

aoss doom3

I had the exact same problem

---

