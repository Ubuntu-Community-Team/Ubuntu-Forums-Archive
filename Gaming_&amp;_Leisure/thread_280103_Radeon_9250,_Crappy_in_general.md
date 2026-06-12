---
title: "Radeon 9250, Crappy in general"
date: 2006-10-18
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2006-10-18
Even though the games I play have versions for Linux, my video card, a Radeon 9250, doesn't work too well. Using whatever driver is with Ubuntu by default, some games have odd graphical glitches and others are not completely playable even on the lowest settings (when on Windows they could run great at much higher settings). Installing the fglrx driver fixes the graphical glitches I had in certain games, but makes every game run very, very slow (probably 1 FPS).

---

### Post by voided3 on 2006-10-19
Hello, I have a Radeon 9250, and I followed these directions to get it to work perfectly:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

In games i get between 45 and 120 FPS with a 2000+ "glxgears -print fps" score, and that's on AGP 4x. One thing to bear in mind, I think the 9200 Pro and the 9250 use the same chip, so mine is recognized as a RV280 9200 PRO, but works just the same. Good luck!

---

### Post by noerrorsfound on 2006-10-29
I had already done that, but the problem was that games ran horribly slow.

I start a game called [Sauerbraten](http://sauerbraten.org/) and the first few seconds (no more than 5) it runs smoothly. Then it's like I'm viewing a slideshow.

The gears thing gives me around 1170 FPS.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
```
```
$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_render_texture
OpenGL renderer string: RADEON 9200 Series DDR Generic
```
```
$ dmesg | grep fglrx
[4294706.346000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294706.349000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[4294706.349000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294707.673000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294707.673000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294707.674000] [fglrx] AGP detected, AgpState   = 0x1f000a0b (hardware caps of chipset)
[4294707.675000] [fglrx] AGP enabled,  AgpCommand = 0x1f000302 (selected caps)
[4294707.687000] [fglrx] total      GART = 134217728
[4294707.688000] [fglrx] free       GART = 118222848
[4294707.688000] [fglrx] max single GART = 118222848
[4294707.688000] [fglrx] total      LFB  = 128970752
[4294707.688000] [fglrx] free       LFB  = 122679296
[4294707.688000] [fglrx] max single LFB  = 122679296
[4294707.688000] [fglrx] total      Inv  = 0
[4294707.689000] [fglrx] free       Inv  = 0
[4294707.689000] [fglrx] max single Inv  = 0
[4294707.689000] [fglrx] total      TIM  = 0
```
Sauerbraten is also the game that runs fine before I follow those instructions, except for a little glitch where the textures are streaky/striped. But that problem is fixed after I follow the instructions. It's too bad about the slideshow.

```
$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
```
I'm wondering about where it says "fglrx: libGL version does not match - OpenGL module is using glapi fallback". In /usr/lib there's two versions of libGL, libGL.so.1 and libGL.so.1.2. The 1.2 is the one I had to replace to fix OpenGL.

---

### Post by jc87 on 2006-10-30
Follow this [guide](https://help.ubuntu.com/community/RadeonDriver)

I have now about **2300 fps with glxgears**:mrgreen: (same Graphic card as you)

If you want here is my [xorg.conf](http://clientes.netvisao.pt/xw166644/xorg.conf)

---

### Post by noerrorsfound on 2006-10-30
Well that guide has reduced my fps in glxgears to 150. :( 

Are you sure you have a 9250 and not a 9200?

---

### Post by jc87 on 2006-10-30
> **noerrorsfound said:**
> Well that guide has reduced my fps in glxgears to 150. :( 

Are you sure you have a 9250 and not a 9200?

Yes, it appears identified as an 9200 (at my xorg.conf), but is a 9250 (the windows driver identifies it as that), and anyway does not matter since is the same chipset :

```

**rv280 / M9+**

Radeon 9200SE
Radeon 9200
Radeon 9250
```

You probably must have done something wrong, re-check with attention all the steps in the guide, specially if the **radeon** driver is properly loaded, and the **fglrx** not loaded.

---

### Post by noerrorsfound on 2006-10-31
The only problem there is is when I have to enter this:
$ glxinfo | grep "direct rendering"

> If it says Yes then you are using the radeon driver, and if it says no then the system may have reverted back to the ati driver. If this is the case then either try the tweaks below or try starting again, making sure your card is supported.
It says no. I've done all the steps it has told me to once more and it's still no.

---

