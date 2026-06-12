---
title: "Openarena and ubuntu 17.04"
date: 2017-07-07
forum: Gaming &amp; Leisure
---

### Post by dimas869 on 2017-07-07
i did installed openrena with this command sudo apt-get install -f openarena

and this is what i get from trying to see the Demo inside the game
```
:~$ openarena
ioq3 1.36+u20161101+dfsg1-1/Ubuntu linux-x86 Nov  5 2016
Have SSE support
----- FS_Startup -----
We are looking in the current search path:
/home/graamont/.openarena/baseoa
/usr/lib/openarena/baseoa
/usr/lib/openarena/baseoa/z_oacmp-volume1-v3.pk3 (370 files)
/usr/lib/openarena/baseoa/pak6-patch088.pk3 (711 files)
/usr/lib/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/openarena/baseoa/pak0.pk3 (1042 files)

----------------------
5803 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
Trying to load "renderer_opengl1_x86.so" from "/usr/lib/ioquake3"...
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Display aspect: 1.779
...setting mode 3: 640 480
Using 24 color bits, 24 depth, 8 stencil display.
Available modes: '1366x768'
GL_RENDERER: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
Initializing OpenGL extensions
...GL_EXT_texture_compression_s3tc not found
...ignoring GL_S3_s3tc
...using GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic
Initializing Shaders

GL_VENDOR: Intel Open Source Technology Center
GL_RENDERER: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 17.0.3
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
----- finished R_Init -----
------ Initializing Sound ------
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Allocated 96 sources.
OpenAL default capture device is 'Built-in Audio Analog Stereo'
OpenAL capture device opened.
OpenAL info:
  Vendor:         OpenAL Community
  Version:        1.1 ALSOFT 1.17.2
  Renderer:       OpenAL Soft
  AL Extensions:  AL_EXT_ALAW AL_EXT_BFORMAT AL_EXT_DOUBLE AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_MULAW AL_EXT_MULAW_BFORMAT AL_EXT_MULAW_MCFORMATS AL_EXT_OFFSET AL_EXT_source_distance_model AL_LOKI_quadriphonic AL_SOFT_block_alignment AL_SOFT_buffer_samples AL_SOFT_buffer_sub_data AL_SOFT_deferred_updates AL_SOFT_direct_channels AL_SOFT_loop_points AL_SOFT_MSADPCM AL_SOFT_source_latency AL_SOFT_source_length
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_DEDICATED ALC_EXT_disconnect ALC_EXT_EFX ALC_EXT_thread_local_context ALC_SOFTX_device_clock ALC_SOFT_HRTF ALC_SOFT_loopback ALC_SOFT_pause_device
  Device:         Built-in Audio Analog Stereo
  Available Devices:
Built-in Audio Analog Stereo
  Input Device:   Built-in Audio Analog Stereo
  Available Input Devices:
Built-in Audio Analog Stereo
Monitor of Built-in Audio Analog Stereo
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
File "vm/ui.qvm" found in "/usr/lib/openarena/baseoa/pak6-patch088.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch088/ui
Loading DLL file /usr/lib/openarena/baseoa/pak6-patch088/uix86.so instead.
Loading DLL file: /usr/lib/openarena/baseoa/pak6-patch088/uix86.so
Sys_LoadGameDll(/usr/lib/openarena/baseoa/pak6-patch088/uix86.so) found vmMain function at 0x94426bc0
71 arenas parsed
33 bots parsed
--- Common Initialization Complete ---
IP: 127.0.0.1
IP: 192.168.1.5
IP: 10.42.0.1
IP6: ::1
IP6: fe80::b7e7:e57e:e79f:cb52%eth0
IP6: fe80::1e4b:d6ff:fe45:ec6f%wlan0
Opening IP6 socket: [::]:27960
Opening IP socket: 0.0.0.0:27960
----- FS_Startup -----
We are looking in the current search path:
/home/graamont/.openarena/baseoa
/usr/lib/openarena/baseoa
/usr/lib/openarena/baseoa/z_oacmp-volume1-v3.pk3 (370 files)
/usr/lib/openarena/baseoa/pak6-patch088.pk3 (711 files)
/usr/lib/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/openarena/baseoa/pak0.pk3 (1042 files)
    
handle 1: demos/demo088-test1.dm_71
----------------------
5803 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----
Initializing Shaders
    
GL_VENDOR: Intel Open Source Technology Center
GL_RENDERER: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 17.0.3
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8
    
PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
----- finished R_Init -----
Loading vm file vm/ui.qvm...
File "vm/ui.qvm" found in "/usr/lib/openarena/baseoa/pak6-patch088.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch088/ui
Loading DLL file /usr/lib/openarena/baseoa/pak6-patch088/uix86.so instead.
Loading DLL file: /usr/lib/openarena/baseoa/pak6-patch088/uix86.so
Sys_LoadGameDll(/usr/lib/openarena/baseoa/pak6-patch088/uix86.so) found vmMain function at 0x94426bc0
71 arenas parsed
33 bots parsed
Loading vm file vm/cgame.qvm...
File "vm/cgame.qvm" found in "/usr/lib/openarena/baseoa/pak6-patch088.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch088/cgame
Loading DLL file /usr/lib/openarena/baseoa/pak6-patch088/cgamex86.so instead.
Loading DLL file: /usr/lib/openarena/baseoa/pak6-patch088/cgamex86.so
Sys_LoadGameDll(/usr/lib/openarena/baseoa/pak6-patch088/cgamex86.so) found vmMain function at 0x86f186c0
tty]Segmentation fault (core dumped)
```

---

### Post by deadflowr on 2017-07-08
Seems like the crashing is a known issue:[lpbug]1651561[/lpbug]
Sorry best I can do.

---

