---
title: "ATi"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Cybercool on 2005-10-19
Hello,

I'm still having trouble getting my ati to run as normal.
I used to run Ubuntu 4.10 and i had no trouble with the 2d interface. (never tested the 3d)

Now the 2d is not working fast at all. And when I check my fgl_glxgears score with other ati people it's much to low. I get arround 300fps.
And with glxgears i get a score of 1500 fps.

I know that in 4.10 it was 6000 fps. So someting is wrong!!

Has anyone got an idea of what can be wrong?
Please help me!!

greetingz, Cybercool

---

### Post by GazaM on 2005-10-19
Cybercool, could you provide more information please? Such as what card you have, which drivers you are using, etc.

If you have breezy and are using the fglrx drivers from the repos you should know some things... you also need to have the appropriate 'restricted-modules' package installed, as it contains the fglrx kernel module (among others) and is required to have working 3d... In fact a missing or mismatched kernel module is the most common issue in fglrx which causes 3D to fail.

Also, which render string does glxinfo output, look for the lines:

OpenGL vendor string: [something]
OpenGL renderer string: [something]
OpenGL version string: [something]

and paste yours in a reply. All of this information will help us help you, a logfile probably isnt necessary just yet, as it is most likely a common problem and should be easy to fix.

---

### Post by Cybercool on 2005-10-19
Sorry i forgot the information:

I have an ati radeon 9000.
I installed the fglrx-xorg, fglrx-config, restricted-kernel

Here under there is my glxinfo output and my fglrxinfo output.


My glxinfo output:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
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
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)
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

my fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

```

---

### Post by GazaM on 2005-10-19
Ok the render string etc. seems to be in order... have you run the fglrxconfig program to create a new xorg.conf? It is most likely just a bad xorg.conf causing suboptimal performance.

But just one other thing... glxgears and fgl_glxgears are not really meant as benchmarking tools, but even so, you say you used to get 6000fps with your 9000, I seriously doubt this as with my X700Pro (all set up working very well, including doom3 etc.) I get just under 5,000 fps on average in glxgears... you get my point :P Not calling you a liar but perhaps something was messed up in warty with glxgears, as your current scores seam more realistic. My advice is to test out a 3d game, such as ET and then you will know if something is truly wrong ;)

[edit] In fact I'm pretty sure those scores are about right for your card, have you noticed any difference in your desktop performance etc?

---

### Post by Cybercool on 2005-10-19
> **GazaM]Ok the render string etc. seems to be in order... have you run the fglrxconfig program to create a new xorg.conf? It is most likely just a bad xorg.conf causing suboptimal performance.

But just one other thing... glxgears and fgl_glxgears are not really meant as benchmarking tools, but even so, you say you used to get 6000fps with your 9000, I seriously doubt this as with my X700Pro (all set up working very well, including doom3 etc.) I get just under 5,000 fps on average in glxgears... you get my point :P Not calling you a liar but perhaps something was messed up in warty with glxgears, as your current scores seam more realistic. My advice is to test out a 3d game, such as ET and then you will know if something is truly wrong  said:**
>  In fact I'm pretty sure those scores are about right for your card, have you noticed any difference in your desktop performance etc?

I try to look for the xorg.conf because i made it with the fglrxconfig.
Also i have to say that the performance in gnome is badder that the installation 4.10 that i had a year ago. 
Thanks for youre help anyway

---

### Post by Dolphin on 2005-10-19
1500fps for a Radeon 9000 sounds right.

You say you used to get 6000fps on a Radeon 9000?  I call shens.

---

### Post by GazaM on 2005-10-19
I agree with Dolphin... that glxgears fps sounds fine for your card really. Gnome performance being slightly worse could be a few things, it may also be in your head because of that glxgears score making you paranoid ;) Really though, dont worry about it, everything seems to be fine. If you can play any games on a Radeon 9000 at any rate, you are doing ok :D

---

