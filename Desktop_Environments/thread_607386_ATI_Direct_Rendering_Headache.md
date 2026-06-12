---
title: "ATI Direct Rendering Headache"
date: 2007-11-08
forum: Desktop Environments
---

### Post by thrillhouse on 2007-11-08
I know there are a million other ATI direct rendering posts on this site but I've been looking for weeks and haven't been able to find anything that will work.  Glxgears crashes my X session.  and when I move windows around there is a significant delay from where it should be and where the window is.  Certain programs are almost unusable because of how badly the scrolling functions.  The hardware is a ATI Radeon Mobility 7500.

Here is the output of glxinfo when I boot with the normal Gnome session.

```
mueller@kinnick:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Four lines to note are as follows:
direct rendering: No
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

I'm pretty sure all three of those things are related (note the Mesa version number).

If I logout and log in using the Failsafe Terminal session, glxgears works fine (400 something fps) and glxinfo outputs the following:

```
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

Those same lines as before are now:
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

How can the graphics system work great in the failsafe terminal and not in the regular gnome session?  Is it because the display names are different, and if so how can I fix this?  Let me know if you need any more information about this and I will gladly post it.  Thank you!!

---

### Post by pay on 2007-11-08
Post your xorg.conf

---

### Post by thrillhouse on 2007-11-08
Kind of thought that would get asked for.  X server uses the same xorg.conf for all the session though right?  So this shouldn't make a difference right??

```

Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/CID"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	# paths to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"EmulateWheel"	"true"
	Option		"EmulateWheelButton"	"2"
	Option		"Protocol"	"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Boardname	"ATI Rage Mobility"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#  	screen 0 "Default Screen" 0 0
	screen 1 "Default Screen" 1 1
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Option		"AIGLX"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Rage Mobility"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by pay on 2007-11-09
Driver		"ati"
should be 
Driver		"fglrx"

Mske sure you have xorg-driver-fglrx installed first

---

### Post by Jouke74 on 2007-11-09
Just enable the restruicted driver will do the same (and has the advantage that it can be disabled in case it fails).

---

### Post by thrillhouse on 2007-11-09
I was under the impression that the fglrx driver wasn't for the radeon 7500.  Not sure if this makes a difference but lspci reports that this is a radeon 7500.  The entry in xorg.conf is from running dpkg-reconfigure xserver-xorg.  Either way, I gave it a shot.  Here is the glxinfo output:

```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)
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
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

The second line 'Xlib:  extension "XFree86-DRI" missing on display ":1.0".' seems like it is the problem, but I still don't know what I need to do to fix it.

---

### Post by thrillhouse on 2007-11-09
Scratch that.  Changing it to 'fglrx' makes x run in safe graphics mode 800x600.  And I can't get it out without switching it back to ati or radeon.

---

### Post by pay on 2007-11-10
Oh sorry I missed what card you were using. Try adding drm to modules```
Section "Module"
        Load "drm"
        ...
EndSection

```Try putting the driver as radeon```
Section "Device"
        Identifier  "ATI Radeon"
        VendorName  "ATI Technologies Inc"
        Driver      "radeon"
        Option          "XAANoOffscreenPixmaps"
        ...
EndSection
```If that doesn't work put it back to ati. You might need to try this```

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```And you could try reading this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Good luck:)

---

### Post by thrillhouse on 2007-11-11
Ok.  Tried what you suggested in your post and then followed the directions in the link.  No dice.  I'm actually basically back to where I started.  glxgears crashes x.  Here is the output from glxinfo, my xorg.conf, and xorg.0.log

glxinfo:
```
mueller@kinnick:~$ glxinfo
name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

xorg.conf
```
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/CID"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	# paths to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	#	Load	"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	
	#Added 10/22/04
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
	Load		"drm"
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
	Option		"Device"	"/dev/input/mice"
	Option		"EmulateWheel"	"true"
	Option		"EmulateWheelButton"	"2"
	Option		"Protocol"	"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Boardname	"ATI Rage Mobility"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	#	SubSection "Display"
	#		Depth		4
	#		Modes		"1024x768"
	#	EndSubSection
	#	SubSection "Display"
	#		Depth		8
	#		Modes		"1024x768"
	#	EndSubSection
	#	SubSection "Display"
	#		Depth		15
	#		Modes		"1024x768"
	#	EndSubSection
	#	SubSection "Display"
	#		Depth		16
	#		Modes		"1024x768"
	#		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	#	EndSubSection
	#	SubSection "Display"
	#		Virtual 1400 1050
	#		Depth		24
	#		Modes		"1400x1050" "1280x1024"  "1024x768" "800x600" "640x480"
	#		Modes		"1024x768"
	#	EndSubSection
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

xorg.0.log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux kinnick 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 11 11:16:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "true"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3340 card 1014,0529 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,052d rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,052e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1014,052d rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,052d rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0537 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1014,0524 rev 01 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c57 card 1014,0530 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 104c,ac46 card 4000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:00:1: chip 104c,ac46 card 4800,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:01:0: chip 8086,101e card 1014,0549 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 168c,1014 card 17ab,8331 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
	[8] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[9] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[10] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[11] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[12] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[13] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[14] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[15] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
	[16] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[17] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[18] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[19] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xcfffffff (0xfe00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:0:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (2:0:1), (2,7,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xec000000 - 0xefffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xe0000000/27, 0xc0100000/16, I/O @ 0x3000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[3] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[4] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[5] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[6] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[7] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[14] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[16] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[3] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[4] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[5] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[6] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[7] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[11] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[14] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[16] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[7] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[8] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon Mobility M7 LW (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[7] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[8] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[17] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[7] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[8] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[23] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[25] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0xe0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1024x768
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Port4: DDCType-0, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 2
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): Using LVDS Native Mode
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-D
 DAC Type  -- None
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- Proprietary/LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): Port3:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
finished output detect: 1
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
finished output detect: 2
finished output detect: 3
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0210000 - 0xc021ffff (0x10000) MX[B]
	[7] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[8] -1	0	0xc0240000 - 0xc025ffff (0x20000) MX[B]
	[9] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[10] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[11] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[12] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[23] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xe0000000,0x2000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x900000
(II) RADEON(0): Will use depth buffer at offset 0xc00000
(II) RADEON(0): Will use 17408 kb for textures at offset 0xf00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0b29000
(II) RADEON(0): [drm] mapped SAREA 0xe0b29000 to 0xb7b49000
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x3340; Card 0x1002/0x4c57]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7a48000
(II) RADEON(0): [agp] ring read ptr handle = 0xd0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7a47000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb5773000
(II) RADEON(0): [agp] GART texture map handle = 0xd0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb5293000
(II) RADEON(0): [drm] register handle = 0xc0100000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd07fd000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd07fd000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): Option "XaaNoOffscreenPixmaps"
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Option "EmulateWheel" "true"
(**) Option "EmulateWheelButton" "2"
(==) Configured Mouse: YAxisMapping: buttons 4 and 5
(**) Configured Mouse: EmulateWheel, EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 2
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
SetClientVersion: 0 9
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(WW) RADEON(0): DDC2/I2C is not properly initialized
(II) RADEON(0): DDC Type: 0, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 2
(II) RADEON(0): Output LVDS connected
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x960" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1280x800" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1152x768" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1152x864" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
```

Thanks :)

---

### Post by thrillhouse on 2007-11-15
Failsafe Gnome works 100% with the display.  A couple other things don't work though, so a combination of these two start ups would be ideal.  Where can I find the start up scripts for Failsafe Gnome and regular Gnome?

---

### Post by Nedtlele on 2007-11-28
Sorry I can't help with your problem, but I see it is a week past, and no replies. 
I am in a similar position, Ati 1900, with Direct Rendering : no

Is there no fixes for this?, I have searched everywhere and find nothing ( as usual I might add)  but out dated threads, with no solutions & slim on direct informaiton.

I am starting to see why Linux has such a low user base, threads like this go weeks without replies, as if there's only one person with the issue.

If Ubuntu would like to increase it's user base, I would help to get issues like this resolved and have 'Stickies' showing clearly how to get the job done.

Surely someone knows how to get a driver to install and have direct rendering enabled. Or is it recommended to just increase dosage of headache tablets to subdue the effect.

---

### Post by xfearxnxloathing on 2007-12-06
This is the only soothing thread on this whole matter, I feel better now that someone has said this.  As a new linux user and in love with Ubuntu/Compiz Fusion like many of you who will read this having the same _**blah issues**_ as the rest of us, I hope this gets resolved very soon or it's back to Windows XP...

:mad:

*> Just because we're newbs to linux doesn't mean we cant follow correct directions!*

---

### Post by JoshuaRL on 2007-12-23
[http://ubuntuforums.org/showthread.php?t=580134](http://ubuntuforums.org/showthread.php?t=580134)

Try that for the Inspiron 5100.  Might work.

---

