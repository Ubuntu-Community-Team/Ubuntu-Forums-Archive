---
title: "Yet another Alien Arena issue"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by deviant on 2008-03-29
Hello. 
As the title states, I`m having a bit of a problem with Alien Arena.
It just won`t run, I tried both the downloaded version and the repo version. I get the same error.
I did some google-ing, but I found nothing relevant.

```
itch@Sisif:~$ alien-arena 
using /home/itch/.alien-arena/data1/ for writing
using /home/itch/.alien-arena/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 7.0.1
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays 
...allowing CDS
...GL_EXT_compiled_vertex_array not found
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
crx.sdl: ref_gl/r_refl.c:133: R_init_refl: Assertion `(err = qglGetError()) == 0x0' failed.
Received signal 6, exiting...
```

My box is a Dell notebook with Intel GMA 945 video card, running Ubuntu 7.10 (32bit) up-to-date.
Does anybody have a clue about what i`ve did wrong ?

---

### Post by deviant on 2008-03-31
*BUMP*
Common, there must be somebody out there who has a clue regarding my problem ..

---

### Post by slimdog360 on 2008-03-31
> ...GL_EXT_compiled_vertex_array not found
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
crx.sdl: ref_gl/r_refl.c:133: R_init_refl: Assertion `(err = qglGetError()) == 0x0' failed.

I would suggest that your dedicated Intel GMA 945 is not good enough to run the game. Sorry.

---

