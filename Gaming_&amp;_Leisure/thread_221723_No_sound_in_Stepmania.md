---
title: "No sound in Stepmania"
date: 2006-07-23
forum: Gaming &amp; Leisure
---

### Post by chibiusa255 on 2006-07-23
I've installed Stepmania and installed all the files I needed to get it up and running without any problems. Everything is working except I don't have any sound in the game. I don't have any sound in the menus and when I start a song the music dosn't start. 
Here's what I get in the console:
> StepMania 3.9
Log starting 2006-07-23 23:44:05
Loading window: gtk
OS: Linux ver 020615
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.3.6
Threads library: NPTL 2.3.6
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
ALSA Driver: 0: Intel 82801DB-ICH4 [I82801DBICH4], device 0: Intel ICH [Intel 82801DB-ICH4], 1/1 subdevices avail
ALSA Driver: 0: Intel 82801DB-ICH4 [I82801DBICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958], 1/1 subdevices avail
ALSA device overridden to "default"
ALSA: Got 32 hardware buffers
Sound driver: ALSA
Video renderers: 'opengl'
SDL version: 1.2.9
Got 32 bpp (8888), 24 depth, 8 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: Tungsten Graphics, Inc
OGL Renderer: Mesa DRI Intel(R) 852GM/855GM 20050225
OGL Version: 1.3 Mesa 6.4.1
OGL Extensions: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
OGL Max texture size: 2048
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: yes
X server vendor: The X.Org Foundation [7.0.0.0]
Server GLX vendor: SGI [1.2]
Client GLX vendor: SGI [1.4]
Fullscreen 640x480 16 color 16 texture 0Hz Vsync AA
Found 0 joysticks
/////////////////////////////////////////
WARNING: RageBitmapTexture: Couldn't load : No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: ScreenExit: 9 sounds failed to finish playing quickly: Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common coin.ogg; Themes/default/Sounds/Common back.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common back.ogg;
/////////////////////////////////////////
Players joined: P1
Language: english
Current renderer: OpenGL
Theme: default


Anyone have any ideas?

---

### Post by ookami on 2006-11-06
I'm having pretty much the same problem on a quite fresh Edgy-install. I had it running on Dapper after some serious tweaking. Any ideas?

```
StepMania 3.9
Log starting 2006-11-06 23:02:19
Loading window: gtk
OS: Linux ver 020617
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.4
Threads library: NPTL 2.4
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
ALSA Driver: 0: NVidia CK8 [CK8], device 0: Intel ICH [NVidia CK8], 0/1 subdevices avail
ALSA Driver: 0: NVidia CK8 [CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958], 1/1 subdevices avail
ALSA device overridden to "default"
ALSA: Got 32 hardware buffers
Sound driver: ALSA

(stepmania:2217): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(stepmania:2217): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
SDL version: 1.2.10
Got 32 bpp (8880), 24 depth, 0 stencil
OGL Vendor: NVIDIA Corporation
OGL Renderer: unknown board/AGP/SSE/3DNOW!
OGL Version: 1.5.8 NVIDIA 96.25
OGL Extensions: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
OGL Max texture size: 4096
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: yes
X server vendor: The X.Org Foundation [7.1.1.0]
Server GLX vendor: NVIDIA Corporation [1.4]
Client GLX vendor: NVIDIA Corporation [1.4]
Windowed 1024x768 32 color 32 texture 0Hz Vsync AA
Found 2 joysticks
   0: 'WiseGroup.,Ltd MP-8866 Dual USB Joypad' axes: 6, hats: 0, buttons: 12
   1: 'WiseGroup.,Ltd MP-8866 Dual USB Joypad' axes: 6, hats: 0, buttons: 12
/////////////////////////////////////////
WARNING: RageBitmapTexture: Couldn't load : No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: ScreenExit: 11 sounds failed to finish playing quickly: Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common back.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common coin.ogg; Themes/default/Sounds/Common back.ogg; Themes/default/Sounds/Common coin.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common start.ogg; Themes/default/Sounds/Common back.ogg; 
/////////////////////////////////////////
Players joined: P1
Language: english
Current renderer: OpenGL
Theme: default
```

---

### Post by ookami on 2006-11-06
Ok, so it seems as if the fixes I did to make Stepmania work under Dapper were the cause of it not working in Edgy. I just moved the Stepmania/Data/StepMania.ini file to let SM start with fresh settings and it worked fine, thus it should work out of the box on Edgy.

---

