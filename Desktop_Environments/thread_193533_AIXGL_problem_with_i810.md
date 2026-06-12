---
title: "AIXGL problem with i810"
date: 2006-06-10
forum: Desktop Environments
---

### Post by jhs_s on 2006-06-10
Hi!

I followed the AIXGL howto and installed all packages (compiz-vanilla, etc.)! When starting up Gnome I don't get any window manager at all because compiz obviously fails starting. Starting compiz from command-line, I get the following:

```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

I only found similar a problem on google with nvidia or ati drivers which replace libGL.so.1.2. Anyway, I checked the library and it contains GLX_EXT_texture_from_pixmap and compiz is linked to exactly this libarary.

My Hardware:
HP nx6110
Intel i915 (with i810 driver from the compiz repositry)
Pentium M 1.73 Mhz
Centrino WLan

Thanks for any ideas!

Johannes

---

### Post by killbill on 2006-06-10
I dunno. coz I'm having the same problem with intel 845G.

And there are lot's of people suffering from this too.

Hope new package of aiglx / compiz will fix this.

---

### Post by jpetro2 on 2006-06-11
Same problem with Asus M2400N and I855 chipset.
I am using the i810 driver, but kernel loads i915.

Is this same stuff or something wrong?

Greetings, 
Jure

---

### Post by jpetro2 on 2006-06-11
After checking 'ps aux' I found out that I am still
running Xorg and not Xorg-air server....

I don't know how could this happen, since I changed 
gdm.conf-custom. (Maybe gdm doesn't correctly parse spaces?)

Anyhow, now that ps aux shows /usr/bin/Xorg-air as a running process
everything works just fine. Hope this helps someone...


Greetings, 
Jutr

---

### Post by Chordonblue on 2006-06-11
Yes, I too spent hours following the GLX/Nvidia instructions to no avail. I mean, I can continue to use the standard X NV driver, but it really does suck.

I wish this could've been sorted out better before release. I'm really not complaining - just... Wishing. With half the desktop chipsets out there 'owned' by Intel, it seems silly not to be able to get this to work easily.


](*,)

---

### Post by nalmeth on 2006-06-11
what do you get from glxinfo or glxgears

---

### Post by apm on 2006-06-13
[QUOTE=jpetro2]Same problem with Asus M2400N and I855 chipset.
I am using the i810 driver, but kernel loads i915.[/QUOTE]

Me too. M2400N with Dapper. Kernel loads i915. I don't experience any problems, but I haven't messed with the GL stuff. Only ordinary X with drm. I just wondered why. I come from Debian sarge and have been happy with the i810 driver.

Another problem I have with the M2400N is that the ACPI battery sometimes thinks the the battery is empty (only for a short while), and that's enough to trigger shutdown (very annoying). I had to disable the reaction to critical low battery power since it could happen at any time. ... do you experience the same? 

PS: I have observed the same behaviour with Sarge... I just didn't think much of it and though it was maybe a problem with the applet.

---

### Post by jhs_s on 2006-06-14
[QUOTE=nalmeth]what do you get from glxinfo or glxgears[/QUOTE]


glxinfo:

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
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
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

glxgears:
```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32

```

glxgears seems to work quite fast anyway (about 700 fps)!

Regards,
Johannes

---

### Post by lalborno on 2006-06-14
I Have aiglx and compiz working fine, but I have the same error when i run a screensaver like glmatrix:

```
lalborno@lalborno-laptop:~$ /usr/lib/xscreensaver/glmatrix
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
lalborno@lalborno-laptop:~$
```


this opens the glmatrix screensaver on a window (and it looks fine, not flickering or slow or anithing), but the content of the window looks always on top, and it does not support transparency, scale, rotate or zoom.

It looks like if the glmatrix is bypassing compiz, even when other applications work fine and compiz does not have any trouble applying the plugins on them, like on firefox, terminal and so on.


I had the same problem with vlc media player but i solved setting X11 Video Output instead of the default.

Anyone knows how to solve this? Please?  :sad:

this is what glxinfo shows:

```
lalborno@lalborno-laptop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
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
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by assan on 2006-06-25
Hello,

I am searching for help with i810 driveron dapper.
I have intel 855GM on laptop. 
trying to install again dri

this is what i have got.
Any hints?

make DRM_MODULES=i810.o modules
make[1]: Wej&#347;cie do katalogu `/home/adrian/i810-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.15-25-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.15-25-686'
  Building modules, stage 2.
  MODPOST
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.15-25-686'
make[1]: Opuszczenie katalogu `/home/adrian/i810-20060403-linux.i386/drm/linux-core'
FATAL: Error inserting i810 (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/i810.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg

[17188816.540000] i810: disagrees about version of symbol drm_open
[17188816.540000] i810: Unknown symbol drm_open
[17188816.540000] i810: disagrees about version of symbol drm_fasync
[17188816.540000] i810: Unknown symbol drm_fasync
[17188816.540000] i810: disagrees about version of symbol drm_poll
[17188816.540000] i810: Unknown symbol drm_poll
[17188816.540000] i810: disagrees about version of symbol drm_core_get_reg_ofs
[17188816.540000] i810: Unknown symbol drm_core_get_reg_ofs
[17188816.540000] i810: disagrees about version of symbol drm_irq_uninstall
[17188816.544000] i810: Unknown symbol drm_irq_uninstall
[17188816.544000] i810: disagrees about version of symbol drm_get_dev
[17188816.544000] i810: Unknown symbol drm_get_dev
[17188816.544000] i810: disagrees about version of symbol drm_ioctl
[17188816.544000] i810: Unknown symbol drm_ioctl
[17188816.544000] i810: disagrees about version of symbol drm_exit
[17188816.544000] i810: Unknown symbol drm_exit
[17188816.544000] i810: disagrees about version of symbol drm_core_get_map_ofs
[17188816.544000] i810: Unknown symbol drm_core_get_map_ofs
[17188816.544000] i810: disagrees about version of symbol drm_init
[17188816.544000] i810: Unknown symbol drm_init
[17188816.544000] i810: Unknown symbol drm_cleanup_pci
[17188816.544000] i810: disagrees about version of symbol drm_mmap
[17188816.544000] i810: Unknown symbol drm_mmap
[17188816.544000] i810: disagrees about version of symbol drm_release
[17188816.544000] i810: Unknown symbol drm_release
[17188844.756000] i810: disagrees about version of symbol drm_open
[17188844.756000] i810: Unknown symbol drm_open
[17188844.760000] i810: disagrees about version of symbol drm_fasync
[17188844.760000] i810: Unknown symbol drm_fasync
[17188844.760000] i810: disagrees about version of symbol drm_poll
[17188844.760000] i810: Unknown symbol drm_poll
[17188844.760000] i810: disagrees about version of symbol drm_core_get_reg_ofs
[17188844.764000] i810: Unknown symbol drm_core_get_reg_ofs
[17188844.764000] i810: disagrees about version of symbol drm_irq_uninstall
[17188844.764000] i810: Unknown symbol drm_irq_uninstall
[17188844.764000] i810: disagrees about version of symbol drm_get_dev
[17188844.768000] i810: Unknown symbol drm_get_dev
[17188844.768000] i810: disagrees about version of symbol drm_ioctl
[17188844.768000] i810: Unknown symbol drm_ioctl
[17188844.768000] i810: disagrees about version of symbol drm_exit
[17188844.768000] i810: Unknown symbol drm_exit
[17188844.768000] i810: disagrees about version of symbol drm_core_get_map_ofs
[17188844.768000] i810: Unknown symbol drm_core_get_map_ofs
[17188844.768000] i810: disagrees about version of symbol drm_init
[17188844.768000] i810: Unknown symbol drm_init
[17188844.768000] i810: Unknown symbol drm_cleanup_pci
[17188844.772000] i810: disagrees about version of symbol drm_mmap
[17188844.772000] i810: Unknown symbol drm_mmap
[17188844.772000] i810: disagrees about version of symbol drm_release
[17188844.772000] i810: Unknown symbol drm_release

---

### Post by Despot on 2006-08-31
(this fix taken from [http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets#Configuring_xorg]("http://gentoo-wiki.com/HOWTO_Direct_rendering_on_Intel_Extreme_Graphics_(855GM)_chipsets#Configuring_xorg"))

Adding a 'VideoRam' option to the Device section in my xorg.conf file fixed this problem for me. Here's the relevant bit: 

> Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        16384
        Option "DRI"    "true"
EndSection

If the VideoRam option is there, try tweaking the value up or down.

---

### Post by bortizc on 2006-10-14
I followed beryl-wiki's instructions
and got AIGLX to work but not beryl.
nonetheless I have noticed that font hinting works better and metacity seems faster.
glxgears works at ~400-500 fps and is very smooth.

I edited xorg-conf to include the video ram setting you suggested and also noticed that the dri option was not enabled.

I still couldn't run beryl
and although I didn't get the libGL warning anymore, glxgears was choppy.

So I switched back to the previous xorg-conf.

I must say that anyhow I'm happy with metacity on AIGLX.
The weird thing is I have tried searching the web to confirm if my perceptions about that are right.
But still I haven't find a single reference.

---

