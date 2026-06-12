---
title: "3ddesktop"
date: 2006-10-11
forum: Desktop Environments
---

### Post by SexyPastry on 2006-10-11
I had to reinstall ubuntu due to errors i kept getting so now when i installed it again i cant use 3ddesktop when it worked perfectly fine before 
i had to reinstall

this is the errror i get:

Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Any ideas?

---

### Post by s_p_a_r_k_y on 2006-10-11
did you install your proprietary video card drivers from nvidia or ati yet? If so, did you add them to your xorg configuration file yet?

If so, can you run glxgears from the console and get something to show up? what about glxinfo

---

### Post by SexyPastry on 2006-10-11
I know my videocard can handle it fine i just dont know wuts wrong this is wut my glxinfo says:

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_ATI_texture_mirror_once, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow
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

---

### Post by s_p_a_r_k_y on 2006-10-11
it doesn't look to me like its using ati or nvidia drivers, depending on which card you have. You should configure it to use those drivers.

---

### Post by x64Jimbo on 2006-10-11
Looks like you need to install the driver for your card. I recommend using Automatix to install that along with all the other stuff that you'll want/need on your system.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by SexyPastry on 2006-10-11
> **x64Jimbo said:**
> Looks like you need to install the driver for your card. I recommend using Automatix to install that along with all the other stuff that you'll want/need on your system.
[www.getautomatix.com](www.getautomatix.com)

I already have that and installed the nvidia drivers and everything is there anything else i  missed. 

How do i configure the nvidia drivers to allow glx?

---

### Post by SexyPastry on 2006-10-11
Thanks guys I got 3ddesktop working.

---

### Post by s_p_a_r_k_y on 2006-10-11
although, now that you have that sexyness, why not try for glx + compiz :) it has made my desktop ueber sexy

---

### Post by PriceChild on 2006-10-11
Or even beryl ;)

Please remember beryl and official compiz are both in beta with major bugs.

Check out my sig if you wanna take the plunge though ;)

---

### Post by SexyPastry on 2006-10-11
> **s_p_a_r_k_y said:**
> although, now that you have that sexyness, why not try for glx + compiz :) it has made my desktop ueber sexy

what is compiz anyway?

---

### Post by s_p_a_r_k_y on 2006-10-11
compiz = sexyness :)

here is a youtube video of it in action,

[http://www.youtube.com/watch?v=-CgqWlX_GsI](http://www.youtube.com/watch?v=-CgqWlX_GsI)

---

### Post by SexyPastry on 2006-10-11
I installed it but how do u do all that stuff on the video?

---

### Post by s_p_a_r_k_y on 2006-10-11
there are numerous forum posts and stuff in google to follow for that already written, do a search for nvidia + compiz or ati + compiz depending on which hardware you have

---

### Post by BLTicklemonster on 2006-10-12
I think you are going to find that finding out anything about beryl or compiz (if you have the experience I am having) is like looking for a needle in a haystack. I haven't posted a wtf on it for fear of the replies I might get, but it all seems pretty mysterious to me. I even attempted to install it, but the config setting for render acceleration would kill x every time I tried to use it.

Can't wait til I can get past that and see what it's all about.

---

