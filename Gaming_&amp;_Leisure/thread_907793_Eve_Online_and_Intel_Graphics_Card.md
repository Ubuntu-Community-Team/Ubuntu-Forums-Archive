---
title: "Eve Online and Intel Graphics Card"
date: 2008-09-01
forum: Gaming &amp; Leisure
---

### Post by Kasuko on 2008-09-01
I just bought a new System76 [Darter Ultra (daru3)]("http://system76.com/product_info.php?cPath=28&products_id=76") and I would like to get eve online working on it. As the website states, this laptop has an Intel X4500HD video card.

Here is my 'eve -config' system specs:
```

cpu: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
cpu_ghz: 1.6
memory: 1976
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) Integrated Graphics Device 4.1.3002
videocard_ram: 2048
agp_aperture_size: N/A
videocard_driver_version: 1.4 Mesa 7.0.3-rc2
soundcard: HDA Intel at 0xf4b00000 irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 64
kernel: 2.6.24-21-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066
```


So I followed the instructions to set it up and it doesn't work. Please help me find out why.

So when I run 'eve' from terminal I first got the splash screen, then I got a black screen. Now when I run it I get:

```
kasuko@ubuntu:~$ eve
Single-user install...
This is the update checker... 
Running /home/kasuko/.cedega/.updater/cedega_updater.py
Running... /home/kasuko/.cedega/.ui/runGUI
kasuko@ubuntu:~$ X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  146 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3607
  Current serial number in output stream:  3609
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  62 (X_CopyArea)
  Resource id in failed request:  0x3a0034d
  Serial number of failed request:  3610
  Current serial number in output stream:  3611
```

So I ran the eve config tests and it states I failed the OpenGL Direct Rendering but passed everything else.

So I ran the debug on the video stuff and got a nice LARGE amount of data that you can find in the eveDebug.log in the attached eveDebug.tar (due to size).

I also looked around the web. Discovered I should post 'glxinfo':
```
kasuko@ubuntu:~$ glxinfo
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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Integrated Graphics Device 4.1.3002
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

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
0x57 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon 
```

also 'glxgears' runs fine. Now "direct rendering: Yes" makes me upset, should it not?

Also I guess I should post my xorg.conf so here it is:
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Anything else you can ask me to post I would be GLAD to get back to you.

Thank you so much for reading all of this.

-Kasuko

---

### Post by Extreme Coder on 2008-09-01
see [http://www.cedega.com/forum/viewtopic.php?t=9630](http://www.cedega.com/forum/viewtopic.php?t=9630)
Apply the Fix (don't worry, Eve Online Linux client is based on Cedega)

---

### Post by Kasuko on 2008-09-01
OK, followed that post.

Now I am stuck with 800x600 resolution and eve goes to a black screen then crashes.

When I redirected the output I got
```
Single-user install...
This is the update checker... 
Running /home/kasuko/.cedega/.updater/cedega_updater.py
Running... /home/kasuko/.cedega/.ui/runGUI
```

which isnt helpful at all.

Anything else?

and why is my resolution screwed now?

Thanks

---

### Post by ex.hav0k on 2008-09-02
im guessing you are using the offical eve client for linux?  i have an ati card and the offical client wouldn't work, but i've had a lot more success using wine.  try installing wine, then installing the eve classic client (windows, not linux) under wine.

---

### Post by MsTBSoX on 2008-09-03
[font=Arial][[size=3][color=red]In 2008 Beijing Olympic Games[/color][/size]](http://wangluozhuanqian.org)[color=silver][size=1] Britain sports delegation has made the [/size][size=1]cmmings[/size][/color][/font][font=Arial][size=1][color=silver] historical progress, wins 19 golden 13 silver 15 copper altogether [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.net)[font=Arial][size=1][color=silver]medals, [/color][/size][/font][[font=Arial][size=1][color=silver]**cmmings**[/color][/size][/font]](http://cmmings.cn/)[font=Arial][size=1][color=silver] arranges in gold medal announcement 4th, and breaks two [/color][/size][/font][[font=Arial][size=1][color=silver]**world**[/color][/size][/font]](http://wangluozhuanqian.org/)[font=Arial][size=1][color=silver] records. Had the historical leap as [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.org)[font=Arial][size=1][color=silver] Olympic Games host country Britain sports.[/color][/size][/font]

---

### Post by Artemis3 on 2008-09-06
> **ex.hav0k said:**
> im guessing you are using the offical eve client for linux?  i have an ati card and the offical client wouldn't work, but i've had a lot more success using wine.  try installing wine, then installing the eve classic client (windows, not linux) under wine.

Wrong, you must install Premium, then choose to use classic content if you want. Follow instructions [here](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=30457&page=74#2203).

---

### Post by NullHead on 2008-09-06
Not related to your plea for help: 

wow, that's one nice laptop :cool:

/me wants one

---

