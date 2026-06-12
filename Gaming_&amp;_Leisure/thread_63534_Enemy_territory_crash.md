---
title: "Enemy territory crash"
date: 2005-09-08
forum: Gaming &amp; Leisure
---

### Post by clapton on 2005-09-08
I've try to play Et on ubuntu but without sucess.

When I run 'et'  appears only the mouse pointer on black background.
And I've got to kill the process, to use other applications

This is the console 
```

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/marco/.etwolf/etmain
/usr/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: RADEON 9550 Generic
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON 9550 Generic
GL_VERSION: 1.3.4769 (X4.3.0-8.8.25)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_texgen_reflection GL_NV_blend_square GL_NV_occlusion_query GL_SGI_color_matrix GL_SGIS_texture_edge_clamp GL_SGIS_texture_border_clamp GL_SGIS_texture_lod GL_SGIS_generate_mipmap GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
------- sound initialization -------
Killed

```
the kill is mine =)

---

### Post by n1ppon on 2005-09-08
[QUOTE=clapton]I've try to play Et on ubuntu but without sucess.

When I run 'et'  appears only the mouse pointer on black background.
And I've got to kill the process, to use other applications

This is the console 
```

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/marco/.etwolf/etmain
/usr/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: RADEON 9550 Generic
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON 9550 Generic
GL_VERSION: 1.3.4769 (X4.3.0-8.8.25)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_texgen_reflection GL_NV_blend_square GL_NV_occlusion_query GL_SGI_color_matrix GL_SGIS_texture_edge_clamp GL_SGIS_texture_border_clamp GL_SGIS_texture_lod GL_SGIS_generate_mipmap GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
------- sound initialization -------
Killed

```
the kill is mine =)[/QUOTE]
 I've got the same problem and I also need some help with this.
If it already have come up in a later thread, can someone please post a link?

---

### Post by clapton on 2005-09-08
I'm not alone ;)
I'm happy, but Plz geeks answer to us.

---

### Post by rimmer on 2005-09-08
[QUOTE=clapton]I'm not alone ;)
I'm happy, but Plz geeks answer to us.[/QUOTE]
It looks like a sound problem: First things first make sure you are not using any other sound programs like xmms, mplayer and totem etc. If you are kill the process and try ET again. 
Any other sound program will block the sound card and ET needs full access to the card it dose not like sharing :(

And your right your not alone have a read of this.
[http://www.ubuntuforums.org/showthread.php?t=5246&page=1&pp=10&highlight=enemy+sound](http://www.ubuntuforums.org/showthread.php?t=5246&page=1&pp=10&highlight=enemy+sound)

---

### Post by clapton on 2005-09-08
I'm turn off every programs that use music.
But the problem of et, can be from any configuration of sound? ](*,)  ](*,) 
I've already read the post of sound issues and I think that not solve my problem.

I've already play et on slackware, before I changed to ubuntu.

---

### Post by clapton on 2005-09-09
No more ideas?

---

