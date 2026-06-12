---
title: "SIS hardware acceleration"
date: 2005-04-30
forum: Gaming &amp; Leisure
---

### Post by az on 2005-04-30
I have an onboard SIS 630 video chip which can do hardware acceleration and is supported by the DRI project:

The details are here:
[http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml)

When I enable dri as described, when I run glxgears, I get an empty black box.  This is better than when I had gotten an error message previously, without having enabled dri.


kurn@ubuntu:~$ glxgears
318 frames in 5.0 seconds = 63.600 FPS
337 frames in 5.0 seconds = 67.400 FPS
308 frames in 5.0 seconds = 61.600 FPS
281 frames in 5.0 seconds = 56.200 FPS
451 frames in 5.0 seconds = 90.200 FPS
457 frames in 5.0 seconds = 91.400 FPS
457 frames in 5.0 seconds = 91.400 FPS
457 frames in 5.0 seconds = 91.400 FPS
447 frames in 5.0 seconds = 89.400 FPS
460 frames in 5.0 seconds = 92.000 FPS
428 frames in 5.0 seconds = 85.600 FPS
459 frames in 5.0 seconds = 91.800 FPS
451 frames in 5.0 seconds = 90.200 FPS


I do not know what number I should be seeing here.  I have seen other posts on the topic, and this does not seem impressive.  Actually, the empty black box is not impressive either.  Would someone know where I should look or what I should do?


kurn@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIS_multisample,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20040925 AGP 1x x86/MMX/3DNow!
OpenGL version string: 1.2 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
kurn@ubuntu:~$

---

### Post by az on 2005-04-30
Right.  I just booted into my Warty partition:

Now, I know that xfree4.3 cannot do dri for the SIS chip without a lot of hacking.  So using an out-of-the-box xfree86 glxgears is visible!

kurn@ubuntu:~ $ glxgears
297 frames in 8.0 seconds = 37.125 FPS
226 frames in 7.0 seconds = 32.286 FPS
226 frames in 6.0 seconds = 37.667 FPS
226 frames in 8.0 seconds = 28.250 FPS
226 frames in 6.0 seconds = 37.667 FPS
226 frames in 7.0 seconds = 32.286 FPS

kurn@ubuntu:~ $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: SGI
client glx version string: 1.2
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 24  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 24  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 24  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 24  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 24  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 24  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 24  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

I would appreciate any help...

---

### Post by Zero Hour on 2005-08-17
I've been fighting this same problem and I'm at the same point as you are heh.
I'm using gentoo but it's all the same. I believe my stuff is fairly up to date, like within the past month'ish at least. I've bewen without net since I just moved so I've been reading over sites that i've saved and man pages and everything out the yang without any net or helps lol. I'm at the same point so I'm still searching for a solution. I've not figured out why drm access is denied for general users except root. Either way I sitll after fidling with the frame buffers and agp and modules and built-in and recompiling the kernel 20 times roughly and man pages and reading and tweaking and all the insane yada yada in my bedroom with no net, I'm at the same point you are. Glxgears and Quake 3 Arena all loads up nicely and zips along, just with a black screen. Not what either of us are looking for so I'm still fighting it and I've been working with it off and on for days. GEEEEEEEEEZ I hate SiS... for years...GIMME MY NVIDIA! :/ You make do with the hardware you have though right?

---

### Post by Zero Hour on 2005-08-17
and you do realize that the reason it's working out of the box right is because the acceleration of any kind is disabled?

---

