---
title: "NO Sound on Openarena"
date: 2010-11-30
forum: Gaming &amp; Leisure
---

### Post by multilinuxuser on 2010-11-30
Kinda a noob at this
 
This is from the output file


```
ioq3+oa 1.35 linux-i386 Dec 18 2009
----- FS_Startup -----
Current search path:
/home/multilinuxuser/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
4163 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.779
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
Available modes: '1366x768 1360x768 640x480 800x600'
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_EXT_texture_compression_s3tc not found
...GL_S3_s3tc not found
...using GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.7.1
GL_EXTENSIONS: GL_EXT_compiled_vertex_array GL_EXT_texture_env_add GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_depth_clamp GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_envmap_bumpmap GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_texture_signed_rgba GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Allocated 96 sources.
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
OpenAL default capture device is 'PulseAudio Capture'
OpenAL capture device opened.
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1 ALSOFT 1.12.854
  Renderer:   OpenAL Soft
  AL Extensions: AL_EXTX_buffer_sub_data AL_EXT_DOUBLE AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_MULAW AL_EXT_MULAW_MCFORMATS AL_EXT_OFFSET AL_EXTX_sample_buffer_object AL_EXT_source_distance_model AL_LOKI_quadriphonic
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_thread_local_context
  Device:     PulseAudio Software
Available Devices:
PulseAudio Software
ALSA Software
OSS Software
PortAudio Software
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1349 jump table targets
VM file ui compiled to 644411 bytes of code
ui loaded in 1398048 bytes on the hunk
41 arenas parsed
24 bots parsed
--- Common Initialization Complete ---
IP: 127.0.0.1
IP: 10.0.235.105
IP6: ::1
IP6: fe80::225:d3ff:fe07:d220%wlan0
Opening IP6 socket: [::]:27960
Opening IP socket: 0.0.0.0:27960
----- CL_Shutdown -----
AL lib: ALc.c:1818: alcCloseDevice(): deleting 8 Buffer(s)
OpenAL capture device closed.
RE_Shutdown( 1 )
-----------------------
```

---

