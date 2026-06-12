---
title: "Opengl problems"
date: 2005-08-08
forum: Gaming &amp; Leisure
---

### Post by halus on 2005-08-08
Hi

Tried to get UFO: Alian Invasion to work on this rather old computer. p2 350Mhz, 192 RAM, and a GF2 with 64 RAM. After following some advices on the net, opengl seems not to work at all. So I can not play chromium as I used to.

$ glxgears
369 frames in 5.0 seconds = 73.800 FPS
339 frames in 6.0 seconds = 56.500 FPS
339 frames in 5.0 seconds = 67.800 FPS


I think I know what I did to destroy the opengl. This command:
set gl_driver "/usr/X11R6/lib/libGL.so.1.2"

I have tried to set other paths to libGL.so.*, and I have tried to reinstall the nvidia drivers. Nothing has helped.

Any suggestions?

---

### Post by charlieg on 2005-08-09
What does the command 'glxinfo' say?

---

### Post by halus on 2005-08-09
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x33 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x34 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x35 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x36 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x37 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x38 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x39 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x3f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x40 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by drummer on 2005-08-09
[quote=halus]OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/quote]There's your problem (not sure about all the other text) but that should say something with nvidia or whatever, not mesa. Mesa is the software opengl renderer. You need to install the drivers for your card, or if you have, they didn't work as they should.

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
or search the forums for the various howtos.

---

### Post by halus on 2005-08-09
Yai, after following the manual to (re)install the driver, opengl and chromium are working.
Thanks.

But I still cant run that UFO game.  ref:

$ ./ufo
execing default.cfg
couldn't exec config.cfg
execing keys.cfg
"K_CTRL" isn't a valid key
Console initialized.

------- sound initialization -------
sound sampling rate: 44100
------------------------------------
------- Loading ref_glx.so -------
LoadLibrary("ref_glx.so"): can't open /etc/quake2.conf
LoadLibrary("./ref_glx.so")
ref_gl version: GL 0.10
QGL_Init("libGL.so"): can't open /etc/quake2.conf
./libGL.so: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "libGL.so"
Dumped console text to ./base/gl_debug.txt.
recursive shutdown
Error: Couldn't initialize OpenGL renderer!
Consult gl_debug.txt for further information.



Installed the game using the loki-installer from here:
[http://www.liflg.org/?catid=6&gameid=16](http://www.liflg.org/?catid=6&gameid=16)

---

