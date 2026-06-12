---
title: "System Constantly Crashing -  Gconf to blame ?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by pear on 2006-06-28
Hi
I have been using Kubuntu for nearly 4 weeks now. I had not had a problem with it until Saturday when I installed Google Earth and it crashed Kubuntu once I had loaded Google Earth. Since then my computer has crashed at various points and with me playing games or just word processing. What seems to happen usually is I lose all input from my keyboard but can still continue to move my mouse (but not click on anything). The sound also continues to come from the speakers. My graphics card makes a noise when it is being used, it goes into overdrive when kubuntu crashes.

First of all the first sign of a problem I have in my logs is:

```
28/06/06 20:37:01	localhost	gconfd (steve-5877)	Exiting

28/06/06 20:37:01	localhost	gconfd (steve-5877)	GConf server is not in use, shutting down.


```

As soon as it shuts down I have a lot of entries similar to this:

```
28/06/06 20:37:46	localhost	kernel	[17186396.560000] pwc leaving VIDIOC_S_FMT, return=0


```

However whilst I get these messages, it appears nothing is wrong to me.

```
28/06/06 20:38:44	localhost	gconfd (steve-6552)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

28/06/06 20:38:44	localhost	gconfd (steve-6552)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

28/06/06 20:38:44	localhost	gconfd (steve-6552)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

28/06/06 20:38:44	localhost	gconfd (steve-6552)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

28/06/06 20:38:44	localhost	gconfd (steve-6552)	Resolved address "xml:readwrite:/home/steve/.gconf" to a writable configuration source at position 1

28/06/06 20:38:44	localhost	gconfd (steve-6552)	starting (version 2.14.0), pid 6552 user 'steve'

28/06/06 20:39:01	localhost	/USR/SBIN/CRON[6560]	(root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

28/06/06 20:39:01	localhost	/USR/SBIN/CRON[6562]	(root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)

28/06/06 20:39:02	localhost	gconfd (root-6572)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

28/06/06 20:39:02	localhost	gconfd (root-6572)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

28/06/06 20:39:02	localhost	gconfd (root-6572)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

28/06/06 20:39:02	localhost	gconfd (root-6572)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

28/06/06 20:39:02	localhost	gconfd (root-6572)	Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1

28/06/06 20:39:02	localhost	gconfd (root-6572)	starting (version 2.14.0), pid 6572 user 'root'

28/06/06 20:44:44	localhost	gconfd (steve-6552)	Exiting

28/06/06 20:44:44	localhost	gconfd (steve-6552)	GConf server is not in use, shutting down.

28/06/06 20:45:03	localhost	gconfd (root-6572)	Exiting

28/06/06 20:45:03	localhost	gconfd (root-6572)	GConf server is not in use, shutting down.

```

I have uninstalled Google Earth but have no idea what else to try. My graphics card is an ASUS EAX300/TD 128MB PCI-E.

---

### Post by disturbed1 on 2006-06-28
To me, it sounds as if Xorg has crashed. Check to make sure x is working properly (glxinfo fglrxinfo), perhaps changes the driver back to ATI for the time being. If you're using XGL turn it off to trouble shoot.

Keyboard stops working <-- contolled by Xorg driver

Using graphics intensive apps <-- Google Earth, Games, some word processors do use OpenGl for rendering parts, Xorg controlled

Graphics card starts to overwork <-- Xorg problem ;).

---

### Post by pear on 2006-06-29
I tried typing in glxinfo and got this repsonse. To me this makes no sense at all.
```

name of display: :0.0
Unknown device ID 5B60, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20040924 TCL
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

I tried typing fglrxinfo but it said command not found.
I also tried sudo dpkg-reconfigure xserver-xorg. But I still have the same problem.

In System Setting > Hardware > Display > Hardware - My graphics card is listed as being ati with the driver ati and below that my ATI Radeon (fglrx) is listed with the driver ati.

I'm sure I'm not using XGL as there is no reference to it anywhere and I haven't made any changes to the setup that was installed, except as I said on Saturday when the GoogleEarth beta seems to have changed something unknowingly.
Will I have to reinstall kubuntu ? I have no idea where my disc is.

---

