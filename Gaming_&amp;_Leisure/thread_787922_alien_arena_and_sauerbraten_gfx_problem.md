---
title: "alien arena and sauerbraten gfx problem"
date: 2008-05-09
forum: Gaming &amp; Leisure
---

### Post by blastradius on 2008-05-09
I've just upgraded to Hardy and have used add/remove to install the two games above. I know my ATI 9600 gfx card is working fine, what happens is that it boots into the games fine but the screen is messed up!
what's happening is that the screen looks fine but over the top of it there is some weird moving patterns going on (can't think of any other way to describe it), this makes it almost impossible to see what's going on.

Here's a bit from glxgears:-

18211 frames in 5.0 seconds = 3642.194 FPS
18280 frames in 5.0 seconds = 3655.865 FPS
18516 frames in 5.0 seconds = 3703.027 FPS
18498 frames in 5.0 seconds = 3699.431 FPS
18511 frames in 5.0 seconds = 3702.042 FPS
18399 frames in 5.0 seconds = 3679.785 FPS

and here's the output when I try to run Alien Arena:-

eric@blastradius:/usr/games$ alien-arena
using /home/blastradius/.alien-arena/data1/ for writing
using /home/blastradius/.alien-arena/arena/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI RADEON 9600 Series
GL_VERSION: 2.1.7412 Release
GL_EXTENSIONS: GL_AMD_performance_monitor GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
------------------------------------
======== CRX Initialized ========

X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 134 (XFree86-VidModeExtension)
Minor opcode of failed request: 10 (XF86VidModeSwitchToMode)
Value in failed request: 0x2e00002
Serial number of failed request: 99
Current serial number in output stream: 101
eric@blastradius:/usr/games$

Please help!

---

