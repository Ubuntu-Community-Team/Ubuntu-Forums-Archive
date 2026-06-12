---
title: "[SOLVED] Nexuiz - Pulseaudio"
date: 2008-08-10
forum: Gaming &amp; Leisure
---

### Post by Bios Element on 2008-08-10
So I've been trying to get Nexuiz to work with pulseaudio for several days now with absolutely no luck. Now the Nexuiz dev's answer is just to totally bypass and disable pulseaudio which I'd really rather not do. So is there any way that i could get 'just' Nexuiz to bypass pulseaudio or better yet, some way to make nexuiz use pulseaudio? I can't be alone in having this problem.

---

### Post by Brebs on 2008-08-10
Nexuiz uses the darkplaces engine, which can be compiled with ALSA, OSS or [SDL sound](http://www.libsdl.org/faq.php?action=listentries&category=3) I think.

Run nexuiz from a console, and show its output. Also try setting the SDL sound system first:
```
export SDL_AUDIODRIVER="alsa"
nexuiz
```

---

### Post by Bios Element on 2008-08-10
This is the terminal output that i got.

```

Nexuiz Linux 15:47:05 May 11 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile data/79drdm5_beta2_nex.pk3 (128 files)
Added packfile data/79drgc2_nex.pk3 (31 files)
Added packfile data/acid3dm5_nex.pk3 (34 files)
Added packfile data/af3hex_nex.pk3 (31 files)
Added packfile data/ame7q3dm3_nex.pk3 (101 files)
Added packfile data/ame7q3tny1_nex.pk3 (53 files)
Added packfile data/apocalyptica_nex.pk3 (27 files)
Added packfile data/bal3dm3_nex.pk3 (69 files)
Added packfile data/bal3dm5_nex.pk3 (63 files)
Added packfile data/batcula_nex.pk3 (62 files)
Added packfile data/chronic_nex.pk3 (154 files)
Added packfile data/CMP1-dm6_nex.pk3 (52 files)
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/cttourney1_nex.pk3 (70 files)
Added packfile data/data20080511.pk3 (4076 files)
Added packfile data/distonic_nex.pk3 (75 files)
Added packfile data/dubneoc_nex.pk3 (22 files)
Added packfile data/geo-core_nex.pk3 (32 files)
Added packfile data/hal_palindrome_nex.pk3 (50 files)
Added packfile data/HandsOfGod_nex.pk3 (32 files)
Added packfile data/ikzdm1_nex.pk3 (141 files)
Added packfile data/jaxtourney2_nex.pk3 (30 files)
Added packfile data/klzegypt_nex.pk3 (91 files)
Added packfile data/ktsdm4_nex.pk3 (36 files)
Added packfile data/map-gleeb_geocomp3_nex.pk3 (28 files)
Added packfile data/mappack.pk3 (1 files)
Added packfile data/mIKEctf2_nex.pk3 (27 files)
Added packfile data/monolith_nex.pk3 (25 files)
Added packfile data/pukka3dm2_nex.pk3 (34 files)
Added packfile data/puma3tourney4_nex.pk3 (29 files)
Added packfile data/q3skoredm1_nex.pk3 (22 files)
Added packfile data/qbeast_nex.pk3 (34 files)
Added packfile data/qdolphin_nex.pk3 (35 files)
Added packfile data/quimera_nex.pk3 (22 files)
Added packfile data/quintdm3_nex.pk3 (63 files)
Added packfile data/redm04_nex.pk3 (64 files)
Added packfile data/storm3dm3_nex.pk3 (75 files)
Added packfile data/straledm5_nex.pk3 (125 files)
Added packfile data/zpdm01_nex.pk3 (38 files)
Trying to load library... "libcurl.so.4" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1440x900x32x60hz
Loading OpenGL driver libGL.so.1
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GT/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_EXT_framebuffer_sRGB GLX_ARB_get_proc_address 
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Shader 'textures/bal3hh/lig_128-01w1-2k' already defined
Shader 'textures/cmp1-dm8/e8trimlight2_pur' already defined
Shader 'textures/cmp1-dm8/e8tinylightpur' already defined
Shader 'textures/cmp1-dm8/e8lighttrim_b_pur' already defined
Shader 'textures/cmp1-dm8/e8lighttrim_pur' already defined
Shader 'textures/cmp1-dm8/e8circle_pur' already defined
Shader 'textures/cmp1-dm8/e8clangfloor' already defined
Shader 'textures/cmp1-dm8/logo' already defined
Shader 'textures/cmp1-dm8/ame7jp' already defined
Shader 'textures/cmp1-dm8/ame7glass' already defined
Shader 'textures/Reaptxt/sun' already defined
Shader 'textures/tech1soc_sfx/lig_032-01b1-2k' already defined
Shader 'textures/tech1soc_sfx/lig_032-05b1-2k' already defined
Shader 'textures/tech1soc_sfx/lig_064-05b1-2k' already defined
Shader 'textures/tech1soc_sfx/lig_128-02y1-2k' already defined
Shader 'textures/tech1soc_sfx/lig_128-03w3-2k' already defined
Shader 'textures/tech1soc_sfx/jpblue_floor01a' already defined
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 44100Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 22050Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 8 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 11025Hz, 8 bit, 1 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: initializing sound output format: 8000Hz, 8 bit, 1 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
SndSys_Init: can't initialize hardware parameters (Operation not permitted)
S_Startup: sound output initialization FAILED
S_Startup: SndSys_Init failed.
CDAudio_SysStartup: open of "/dev/cdrom" failed (2)
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:60601
No CD in player.

```

---

### Post by Brebs on 2008-08-10
Try running the SDL version of nexuiz. Probably called nexuiz-sdl.

---

### Post by Bios Element on 2008-08-11
> **Brebs said:**
> Try running the SDL version of nexuiz. Probably called nexuiz-sdl.

Wow it worked. Amazing. I'll have to remember to go tell the buggers over at the Nexuiz forums about this. Also, would anyone know if there's a wiki page or something that myself or someone could put this tip for others having problems?

---

### Post by Melcar on 2008-08-11
Some of these games come with two binaries; a "normal" .glx one, and a .sdl one.  The .sdl binary usually has less compatibility issues (usually sound related).

---

