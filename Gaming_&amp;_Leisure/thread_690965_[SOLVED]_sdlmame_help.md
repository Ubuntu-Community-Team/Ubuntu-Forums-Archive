---
title: "[SOLVED] sdlmame help"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by gigaferz on 2008-02-08
hello everybody.

 I ve been trying to run sdlmame in my pc for a long time now,.

 Im almost there but when loading a rom it freezes @ initializing, or @ decoding or @ somepoint.

  I have noticed a really poor graphic  performance on my pc  lately since feisty...

 kxmame and wahcade always crash too.(not that matters but the kxmame i got it from these forums and wahcade from the website)

   do i need more graphic "libs" ?

  please help

What kind of  troubleshooting would you do step by step to figure out whats wrong with my machine?

---

### Post by gigaferz on 2008-02-11
well, i tried installing sdlmame and kxmame using a livecd session, and  it also freezes @ decoding or initializing, Do you think is because my roms are in the windows partition?

---

### Post by disturbedite on 2008-02-11
sounds like you might have a graphics driver problem.  you need to post that info...

---

### Post by gigaferz on 2008-02-11
hey!!thanks for answering , however I need to know how to do that...ill post my xorg and the glx info (or something) let me know.

I ve thinking that it could be an usb device too,,,
This is the output of dslmame with the verbose switch enabled, it happens with all the games,it freezes right there, i even left it alone for an hour to see what would happen but it remained the same.

> fer@fer-desktop:~$ sdlmame sfz3a
Parsing mame.ini
Build version:      0.122 (Dec 29 2007)
Build architecure:  SDLMAME_ARCH= 
Build defines:      SDLMAME_UNIX=1 SDLMAME_X11=1 SDLMAME_LINUX=1 LSB_FIRST=1 NDEBUG=1 
SDL/OpenGL defines: SDL_COMPILEDVERSION=1211 USE_OPENGL=1 USE_DISPATCH_GL=1 
Compiler defines A: __GNUC__=4 __GNUC_MINOR__=1 __GNUC_PATCHLEVEL__=3 __VERSION__="4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)" 
Compiler defines B: __unix__=1 __i386__=1 
SDL Device Driver     : x11
SDL Monitor Dimensions: 1680 x 1050
Using SDL single-window soft driver (SDL 1.2)
Input: Adding Kbd #1: System keyboard
Input: Adding Mouse #1: System mouse
Joymap: Start reading joymap_file /etc/sdlmame/joymap.dat
Joymap: Processed 10 lines
Joystick: Start initialization
Input: Adding Joy #1: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10
Joystick: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10
Joystick:   ...  37 axes, 42 buttons 0 hats
Joystick:   ...  Physical id 0 mapped to logical id 0
Input: Adding Joy #2: Logitech Logitech Dual Action
Joystick: Logitech Logitech Dual Action
Joystick:   ...  6 axes, 12 buttons 0 hats
Joystick:   ...  Physical id 1 mapped to logical id 1
Input: Adding Joy #3: Logitech Logitech(R) Precision(TM) Gamepad
Joystick: Logitech Logitech(R) Precision(TM) Gamepad
Joystick:   ...  2 axes, 10 buttons 0 hats
Joystick:   ...  Physical id 2 mapped to logical id 2
Joystick: End initialization
Audio initialized - driver: alsa, frequency: 48000, channels: 2, samples: 1024
sdl_create_buffers: creating stream buffer of 57344 bytes
  
This is the glxinfo I do not know what happened, a couple of days ago i wasnt able to use the effects , and I didnt have the direct rendering enabled, but after using the livecd and always logging to a safe gnome session,
 all of a sudden it started working again (?) but i did install and removed some stuff, i wish there was a log of things that happen to the system
>  fer@fer-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

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
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

this is my last xorg everything is running fine,well There was a time when I had to edit the xorg to display  low resolutions (like 600 x 400 etc) after some updates and a reconfiguration my monitor was detected by "its name" and takes all the resolution (i need them to play games at 400 x 300 @ fullscreen ,for better performance) 
>    # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"AL2216W"
	Option		"DPMS"
	HorizSync	31-84
	VertRefresh	56-77
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by disturbedite on 2008-02-12
well, all i meant was which video card & driver you had.  but the other info will prolly be helpful too.
it just so happens that you have the same exact integrated video chip i do... not that it matters.
so it freezes at:
```
sdl_create_buffers: creating stream buffer of 57344 bytes
```
right?
wish i could help you more, but i don't know where to go from here.
it might be a good idea to post this same info at the [sdlmame forum]("http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1")...

---

### Post by gigaferz on 2008-02-12
, is an intel 845,

I just installed sdlmame on a really  old computer, and runs "fair" , in a little window,but runs.
  Also when i launch sdlmame  (by itself,in my pc) i get the screen with all the games, but is always scrolling up and enter doesnt work ,so i cant choose a game...

  thanks !!

---

### Post by gigaferz on 2008-02-17
After updating the system  and unpluggin my microsoft wireless keyboard and mouse everything works fine.

---

