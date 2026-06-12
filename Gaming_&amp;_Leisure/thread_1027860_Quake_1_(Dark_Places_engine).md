---
title: "Quake 1 (Dark Places engine)"
date: 2009-01-01
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2009-01-01
Hi, I successfully installed the Dark Places engine for Quake using the following guide (second post by billyfoxtrot):

[http://ubuntuforums.org/showthread.php?t=311391](http://ubuntuforums.org/showthread.php?t=311391)

When I start the game attract mode looks perfect without any issues EXCEPT that the bottom graphics (the HUD) looks corrupted, just a bunch of blocks AND sound doesn't work at all. Since I started it from terminal this is the output of it in which you can see that sound initialization failed:

```

moonfrost@moonfrost-desktop:/usr/local/games/quake$ ./darkplaces-linux-x86_64-glx
DarkPlaces-Quake Linux 10:46:32 Oct  4 2008 - release
Trying to load library... "libz.so.1" - loaded.
Added packfile id1/PAK0.PAK (338 files)
Added packfile id1/PAK1.PAK (85 files)
Playing registered version.
Trying to load library... "libcurl.so.4" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Playing demo demo1.dem.
Initializing Video Mode: fullscreen 640x480x32x60hz
Loading OpenGL driver libGL.so.1
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6150 LE/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 177.80
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/disc
Draw_CachePic: failed to load gfx/num_0
Draw_CachePic: failed to load gfx/anum_0
Draw_CachePic: failed to load gfx/num_1
Draw_CachePic: failed to load gfx/anum_1
Draw_CachePic: failed to load gfx/num_2
Draw_CachePic: failed to load gfx/anum_2
Draw_CachePic: failed to load gfx/num_3
Draw_CachePic: failed to load gfx/anum_3
Draw_CachePic: failed to load gfx/num_4
Draw_CachePic: failed to load gfx/anum_4
Draw_CachePic: failed to load gfx/num_5
Draw_CachePic: failed to load gfx/anum_5
Draw_CachePic: failed to load gfx/num_6
Draw_CachePic: failed to load gfx/anum_6
Draw_CachePic: failed to load gfx/num_7
Draw_CachePic: failed to load gfx/anum_7
Draw_CachePic: failed to load gfx/num_8
Draw_CachePic: failed to load gfx/anum_8
Draw_CachePic: failed to load gfx/num_9
Draw_CachePic: failed to load gfx/anum_9
Draw_CachePic: failed to load gfx/num_minus
Draw_CachePic: failed to load gfx/anum_minus
Draw_CachePic: failed to load gfx/num_colon
Draw_CachePic: failed to load gfx/num_slash
Draw_CachePic: failed to load gfx/inv_shotgun
Draw_CachePic: failed to load gfx/inv_sshotgun
Draw_CachePic: failed to load gfx/inv_nailgun
Draw_CachePic: failed to load gfx/inv_snailgun
Draw_CachePic: failed to load gfx/inv_rlaunch
Draw_CachePic: failed to load gfx/inv_srlaunch
Draw_CachePic: failed to load gfx/inv_lightng
Draw_CachePic: failed to load gfx/inv2_shotgun
Draw_CachePic: failed to load gfx/inv2_sshotgun
Draw_CachePic: failed to load gfx/inv2_nailgun
Draw_CachePic: failed to load gfx/inv2_snailgun
Draw_CachePic: failed to load gfx/inv2_rlaunch
Draw_CachePic: failed to load gfx/inv2_srlaunch
Draw_CachePic: failed to load gfx/inv2_lightng
Draw_CachePic: failed to load gfx/inva1_shotgun
Draw_CachePic: failed to load gfx/inva1_sshotgun
Draw_CachePic: failed to load gfx/inva1_nailgun
Draw_CachePic: failed to load gfx/inva1_snailgun
Draw_CachePic: failed to load gfx/inva1_rlaunch
Draw_CachePic: failed to load gfx/inva1_srlaunch
Draw_CachePic: failed to load gfx/inva1_lightng
Draw_CachePic: failed to load gfx/inva2_shotgun
Draw_CachePic: failed to load gfx/inva2_sshotgun
Draw_CachePic: failed to load gfx/inva2_nailgun
Draw_CachePic: failed to load gfx/inva2_snailgun
Draw_CachePic: failed to load gfx/inva2_rlaunch
Draw_CachePic: failed to load gfx/inva2_srlaunch
Draw_CachePic: failed to load gfx/inva2_lightng
Draw_CachePic: failed to load gfx/inva3_shotgun
Draw_CachePic: failed to load gfx/inva3_sshotgun
Draw_CachePic: failed to load gfx/inva3_nailgun
Draw_CachePic: failed to load gfx/inva3_snailgun
Draw_CachePic: failed to load gfx/inva3_rlaunch
Draw_CachePic: failed to load gfx/inva3_srlaunch
Draw_CachePic: failed to load gfx/inva3_lightng
Draw_CachePic: failed to load gfx/inva4_shotgun
Draw_CachePic: failed to load gfx/inva4_sshotgun
Draw_CachePic: failed to load gfx/inva4_nailgun
Draw_CachePic: failed to load gfx/inva4_snailgun
Draw_CachePic: failed to load gfx/inva4_rlaunch
Draw_CachePic: failed to load gfx/inva4_srlaunch
Draw_CachePic: failed to load gfx/inva4_lightng
Draw_CachePic: failed to load gfx/inva5_shotgun
Draw_CachePic: failed to load gfx/inva5_sshotgun
Draw_CachePic: failed to load gfx/inva5_nailgun
Draw_CachePic: failed to load gfx/inva5_snailgun
Draw_CachePic: failed to load gfx/inva5_rlaunch
Draw_CachePic: failed to load gfx/inva5_srlaunch
Draw_CachePic: failed to load gfx/inva5_lightng
Draw_CachePic: failed to load gfx/sb_shells
Draw_CachePic: failed to load gfx/sb_nails
Draw_CachePic: failed to load gfx/sb_rocket
Draw_CachePic: failed to load gfx/sb_cells
Draw_CachePic: failed to load gfx/sb_armor1
Draw_CachePic: failed to load gfx/sb_armor2
Draw_CachePic: failed to load gfx/sb_armor3
Draw_CachePic: failed to load gfx/sb_key1
Draw_CachePic: failed to load gfx/sb_key2
Draw_CachePic: failed to load gfx/sb_invis
Draw_CachePic: failed to load gfx/sb_invuln
Draw_CachePic: failed to load gfx/sb_suit
Draw_CachePic: failed to load gfx/sb_quad
Draw_CachePic: failed to load gfx/sb_sigil1
Draw_CachePic: failed to load gfx/sb_sigil2
Draw_CachePic: failed to load gfx/sb_sigil3
Draw_CachePic: failed to load gfx/sb_sigil4
Draw_CachePic: failed to load gfx/face1
Draw_CachePic: failed to load gfx/face_p1
Draw_CachePic: failed to load gfx/face2
Draw_CachePic: failed to load gfx/face_p2
Draw_CachePic: failed to load gfx/face3
Draw_CachePic: failed to load gfx/face_p3
Draw_CachePic: failed to load gfx/face4
Draw_CachePic: failed to load gfx/face_p4
Draw_CachePic: failed to load gfx/face5
Draw_CachePic: failed to load gfx/face_p5
Draw_CachePic: failed to load gfx/face_invis
Draw_CachePic: failed to load gfx/face_invul2
Draw_CachePic: failed to load gfx/face_inv2
Draw_CachePic: failed to load gfx/face_quad
Draw_CachePic: failed to load gfx/sbar
Draw_CachePic: failed to load gfx/ibar
Draw_CachePic: failed to load gfx/scorebar
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
```

The main issue for me here is sound not working, but if I could get some help with the corrupted HUD that would be nice too. I'm using the data files from an original CD by the way.

---

### Post by Moonfrost on 2009-01-02
Anyone??? I really need help with this! I wanna play Quake on Linux!

---

### Post by Brebs on 2009-01-02
> **Moonfrost said:**
> Draw_CachePic: failed to load gfx/disc
etc.


The graphics appear as square blocks because they aren't being loaded properly. Corrupted files, maybe - what are your exact filesizes and md5sums for the *.pak files?

---

### Post by rs3 on 2009-02-01
> **Moonfrost said:**
> The main issue for me here is sound not working, but if I could get some help with the corrupted HUD that would be nice too. I'm using the data files from an original CD by the way.

I had to kill Pulseaudio to get Darkplaces working.  I've since disabled Pulseaudio from my session startup and just push everything to ALSA (which is what Darkplaces tries to use).  However, I have had intermittent issues with the sound suddenly going mute; your mileage may vary.

---

### Post by pallabbasu1234 on 2009-10-13
I also have the sound issue with darkplaces. There is no sound with pulse audio and linux binary. However windows binary works fine with wine.

---

### Post by Krank on 2010-02-25
> **rs3 said:**
> However, I have had intermittent issues with the sound suddenly going mute; your mileage may vary.

Same here; it seems setting light effects to "high" rather than "full" makes it happen less often...

Tried the windows exe in wine; terrible sound lag (like 1-2 seconds), but not the same "suddenly mute" problem...

---

