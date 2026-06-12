---
title: "XGL + Nvidia / No Direct Rendering"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Shadowfire on 2006-08-04
First things first - Nvidia driver and logo is loading up and seems to be okay. I am able to use all the XGL features too.

Now this issue is to do with the direct rendering = no.  I have been working on this issue for quite a bit now.  I thought I had figure out the solution.  In fact I even had the Direct Rendering saying YES lastnight.  Unfutunately it is not longer working.

My current glxinfo is as follows:
-------------------------------------

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600/PCI/SSE/3DNOW!
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.62)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program,
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_ATI_texture_mirror_once, GL_HP_occlusion_test,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

----------------------------------------------------------------------


I have already done - 

 sudo aptitude remove xserver-xgl
 sudo aptitude reinstall ~nmesa
 sudo aptitude reinstall nvidia-glx

the restarted and reinstalled xserver-xgl

The first time I did this it worked and I saw the glxinfo direct rendering say yes.

Today I have been working on the system and I started to have problems after I installed a game with Cedega.

I then went to glxinfo again to see if it was doing direct rendering and it said no. That is when I tried the above one more time to see if it would re-fix the issue.

Any ideas or help to get me out of this re-occuring issue?  Any help is appreciated.


Thanks,
Shadowfire

---

### Post by exif on 2006-08-04
Perhaps installing the Linux drivers from nVidia's site rather than from the repositories might help. I've heard of a few people doing that and it fixed their problems. Not 100% sure though.

---

### Post by exif on 2006-08-04
I just stumbled over this: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

it'll let you have direct rendering and XGL :D

---

### Post by Shadowfire on 2007-04-06
exif - thanks for the help.  It had to do with not installing my Nvidia drivers properly.  I never got back here to thank you for your replies.. Hopefully better late then never - eh?  

Thanks again,
Shadowfire

---

