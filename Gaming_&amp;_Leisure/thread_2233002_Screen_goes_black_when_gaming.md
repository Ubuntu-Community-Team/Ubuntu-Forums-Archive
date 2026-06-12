---
title: "Screen goes black when gaming"
date: 2014-07-05
forum: Gaming &amp; Leisure
---

### Post by Jenopo on 2014-07-05
I've recently moved form Windows 8.1 to 14.04 Kubuntu and have been particularly glad to have most of my Steam Library become recently available in Linux (I'm sreiously only keeping windows to play my GOG games and one of my Steam favourites).

However and Issue has arisen with my screen turning itself off when I play the following three games; Dota 2, Portal and Rogue Legacy. I've not played all of my Steam library yet but most of my other steam library games work fine thus far. There is no way to get the screen running again and I have to force my computer to reboot. Is anyone else having a similar problem?

EDIT: My computer is a an HP envy m6, I probably should have mentioned it, I'm also running 64 bit Kubuntu currently.

---

### Post by oldrocker99 on 2014-07-05
OK. Your machine has an A6 APU, which has ATI/AMD Radeon HD 7500G graphics. You should try to install the fglrx drivers (AMD/ATI's proprietary graphics driver) for your machine. Look in **Settings/Additional Drivers** and see what is available. I use a five year old AMD Phenom II 965 with an nVidia 650ti, so I'm not a big expert on the fglrx drivers, except to note that, for Linux, ATI's drivers are not as good as they should be. 

BTW, for best game performance with Kubuntu, go to **Settings/System Settings/Desktop Effects/Advanced** and make sure that **Suspend desktop effects for fullscreen windows** is checked. That way, no wobbly windows (or whatever) will affect the game in that window.

---

### Post by Jenopo on 2014-07-05
Cheers for the tip, the proprietary drivers appeared and I installed them/put them to use. I tested them with Portal and it wouldn't run, an error came up stating that my video card was unsupported. 

I've also changed the Desktop effects as you suggested and am about to test that, I'll be back with details.

EDIT: Yeah still having the same problems, and it looks like I can't use the proprietary drivers because the games won't run, any suggestions?

---

### Post by oldrocker99 on 2014-07-06
You might try reinstalling the proprietary drivers.

---

### Post by Jenopo on 2014-07-07
Sorry to be a noob, but what would I need to do for that?

---

### Post by mastablasta on 2014-07-09
that doesn't make sense. are the drivers propperly configured? what is the output of 

```
fglrxinfo
```

command?

you could try removing them and manually downloading and installing a newer version of drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

however A6 should be well supported. can you copy and paste this into terminal and then copy & paste the output here on forums:

```
lspci -vvnn | grep VGA
```

---

### Post by Jenopo on 2014-07-09
Outcome for the command was
```
fglrxinfo: command not found
```

EDIT: after I put in glxinfo

I got ```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD ARUBA
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_AMD_vertex_shader_layer, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_ARB_ES2_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_clear_buffer_object, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_get_program_binary, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_sync, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_float, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_shader, GL_ARB_vertex_type_10f_11f_11f_rev, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_blend_equation_separate, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_sRGB, GL_EXT_packed_depth_stencil, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_provoking_vertex, GL_EXT_texture_array, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_packed_depth_stencil, GL_NV_texture_barrier, GL_NV_vdpau_interop, 
    GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc

OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_NV_vdpau_interop, 
    GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

240 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x048 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x1f2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1fd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fe 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x1ff 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x200 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x201 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x202 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x203 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x204 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x205 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x206 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x207 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x208 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x209 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x20a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x20b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x20c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x20d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x20e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x20f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x210 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x211 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x212 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x213 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x214 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x215 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x216 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x217 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x218 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x219 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x21a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x21b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x21c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x21d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x21e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x21f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x220 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x221 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x222 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x223 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x224 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x225 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x226 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x227 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x228 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x229 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x22a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x22b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x22c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x22d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x22e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x22f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x230 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x231 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x232 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x233 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x234 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x235 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x236 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x237 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x238 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x239 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x23b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x23d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x23f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x240 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x241 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x242 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x243 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x244 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x245 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x246 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x247 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x248 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x249 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x24a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x24b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x24c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x24d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x24e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x24f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x250 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x251 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x252 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x253 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x254 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x255 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x256 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x257 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x258 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x259 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x25a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x25b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x25c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x25d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x25e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x25f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x260 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x261 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x262 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x263 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x264 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x265 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x266 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x267 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x268 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x269 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x26b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x26d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x26f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x270 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x271 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x272 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x273 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x274 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x275 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x276 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x277 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x278 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x279 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x27a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x27b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x27e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x280 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x281 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x282 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x283 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x284 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x285 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x286 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x287 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x288 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x289 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x28a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x28b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x28c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x28d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x28e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x28f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x290 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x291 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x292 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x293 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x294 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x295 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x296 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x297 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x298 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x299 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x29a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x29b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x29c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x29d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x29e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x29f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x2a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x2a2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2aa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2b6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2ba 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2bb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2bc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2bd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2be 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2bf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2c0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2c1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2c2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2c4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2c5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2ca 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2cf 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2d7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2d8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2d9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2da 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2dc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2dd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2de 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x089 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

360 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x08a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x090 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x092 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a0 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0aa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0ac 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0ad 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0b0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0b1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0b4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0b5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0b7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0bc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0bd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0be 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0bf 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0c1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0da 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0de 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0df 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0e8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0f0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fa 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x100 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x101 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x102  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x103  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x104  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x105  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x106  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x107  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x108  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x109  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x110  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x111  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x112  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x113  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x114  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x115  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x116  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x117  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x118  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x119  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x11b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x11c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x11d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x11e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x11f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x120  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x121  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x122  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x123  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x124  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x125  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x126  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x127  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x128  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x129  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x12a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x12b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x12c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x12d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x12e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x12f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x130  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x131  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x132  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x133  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x134  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x135  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x136  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x137  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x138  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x139  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x13a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x13b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x13c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x13d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x13e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x13f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x142 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x143 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x144 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x145 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x146 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x147 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x148 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x149 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x14a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x14c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x14e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x150 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x151 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x152 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x153 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x155 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x156 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x157 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x158 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x159 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x15a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x15b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x15c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x15d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x15e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x15f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x160 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x161 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x162 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x163 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x164 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x165 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x166 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x167 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x168 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x169 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x16a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x16b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x16c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x16d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x16e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x16f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x170 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x171 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x172 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x173 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x174 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x175 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x176 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x177 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x178 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x179 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x17a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x180 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x181 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x182 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x185 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x186 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x187 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x188 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x189 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x18a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x18b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x18c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x18e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x190 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x191 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x192 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x193 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x194 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x195 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x196 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x197 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x198 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x199 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x19a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x19b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x19c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x19d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x19e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x19f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1a5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1a6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1ad 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1b5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1b7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1b8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1b9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1ba  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1bc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1bd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1be  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1c0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1c1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1c2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c3  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1c9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1cc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1cd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1ce  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1cf  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1d2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1d5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1d8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1d9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1da  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1db  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1dc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1dd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1de  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1df  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1e0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ea  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1eb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1ec  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None

 
```

Second one came out with 
```
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G] [1002:990b] (prog-if 00 [VGA controller])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] [1002:6840] (rev ff) (prog-if ff)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

```

---

### Post by oldrocker99 on 2014-07-09
the command you want is

```
glxinfo
```

to get your video information. Good luck!

---

### Post by hbutt875 on 2014-07-09
Contact your video card manufactures

---

### Post by Jenopo on 2014-07-09
cheers guys, posted all the relevant in my last one, is it generally agreed I should remove and reinstall?

---

### Post by oldrocker99 on 2014-07-09
It can't hurt to remove and reinstall. After you do that, try this:

The latest video drivers are in a PPA (personal private archive) and you can add it by thus:

sudo apt-add repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

This will likely upgrade your drivers to the latest versions for Ubuntu.

---

### Post by Peter_Solver on 2014-07-09
> **Jenopo said:**
> cheers guys, posted all the relevant in my last one, is it generally agreed I should remove and reinstall?

I think so. Your video drivers need to be updated and upgraded to a new one.

---

### Post by Jenopo on 2014-07-09
Ran those commands, seemed to work, I used to be able to run the games at first on the Ubuntu standard sources and then it would go black, but now none of the problem games will even open \nd the error reads 

> Could not find required OpenGL Entry Point 'glGetError'! Either your video card is unsupported, or you OpenGL driver needs to be updated.

Steam opens with the following 
```
 OpenGL GLX context is not using direct rendering, which may cause performance problems 
```

Glxinfo returns this
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD ARUBA
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_AMD_vertex_shader_layer, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_ARB_ES2_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shader_stencil_export, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_shader, GL_ARB_vertex_type_10f_11f_11f_rev, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_blend_equation_separate, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_sRGB, GL_EXT_packed_depth_stencil, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_provoking_vertex, 
    GL_EXT_shader_integer_mix, GL_EXT_texture_array, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_packed_depth_stencil, GL_NV_texture_barrier, GL_NV_vdpau_interop, 
    GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc

OpenGL version string: 3.0 Mesa 10.3.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_stencil_texturing, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shader_integer_mix, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_NV_vdpau_interop, 
    GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

240 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x048 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x1f2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x1f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x1f8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x1fd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x1fe 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x1ff 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x200 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x201 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x202 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x203 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x204 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x205 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x206 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x207 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x208 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x209 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x20a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x20b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x20c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x20d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x20e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x20f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x210 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x211 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x212 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x213 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x214 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x215 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x216 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x217 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x218 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x219 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x21a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x21b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x21c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x21d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x21e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x21f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x220 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x221 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x222 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x223 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x224 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x225 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x226 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x227 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x228 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x229 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x22a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x22b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x22c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x22d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x22e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x22f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x230 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x231 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x232 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x233 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x234 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x235 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x236 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x237 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x238 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x239 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x23b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x23d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x23e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x23f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x240 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x241 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x242 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x243 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x244 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x245 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x246 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x247 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x248 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x249 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x24a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x24b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x24c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x24d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x24e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x24f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x250 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x251 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x252 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x253 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x254 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x255 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x256 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x257 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x258 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x259 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x25a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x25b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x25c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x25d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x25e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x25f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x260 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x261 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x262 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x263 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x264 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x265 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x266 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x267 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x268 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x269 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x26b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x26d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x26e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x26f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x270 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x271 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x272 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x273 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x274 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x275 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x276 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x277 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x278 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x279 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x27a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x27b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x27e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x27f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x280 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x281 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x282 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x283 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x284 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x285 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x286 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x287 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x288 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x289 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x28a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x28b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x28c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x28d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x28e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x28f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x290 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x291 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x292 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x293 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x294 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x295 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x296 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x297 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x298 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x299 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x29a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x29b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x29c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x29d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x29e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x29f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x2a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x2a2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x2a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x2a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x2a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2aa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x2ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x2af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x2b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x2b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2b6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x2ba 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2bb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2bc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2bd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2be 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2bf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2c0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2c1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2c2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2c4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2c5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2ca 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2cf 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2d6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2d7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2d8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2d9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2da 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2dc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2dd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2de 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x089 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

360 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x08a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x090 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x092 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x09c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a0 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0aa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0ac 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0ad 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0b0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0b1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x0b4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0b5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0b7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0bc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0bd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0be 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0bf 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0c1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0c6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0da 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0de 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0df 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0e5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0e7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0e8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0f0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0f9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fa 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x100 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x101 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x102  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x103  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x104  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x105  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x106  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x107  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x108  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x109  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x10f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x110  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x111  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x112  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x113  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x114  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x115  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x116  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x117  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x118  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x119  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x11b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x11c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x11d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x11e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x11f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x120  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x121  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x122  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x123  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x124  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x125  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x126  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x127  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x128  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x129  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x12a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x12b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x12c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x12d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x12e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x12f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x130  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x131  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x132  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x133  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x134  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x135  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x136  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x137  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x138  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x139  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x13a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x13b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x13c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x13d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x13e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x13f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x142 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x143 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x144 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x145 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x146 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x147 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x148 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x149 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x14a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x14c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x14e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x14f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x150 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x151 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x152 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x153 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x155 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x156 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x157 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x158 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x159 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x15a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x15b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x15c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x15d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x15e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x15f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x160 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x161 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x162 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x163 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x164 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x165 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x166 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x167 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x168 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x169 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x16a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x16b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x16c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x16d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x16e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x16f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x170 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x171 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x172 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x173 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x174 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x175 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x176 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x177 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x178 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x179 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x17a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x180 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x181 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x182 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x185 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x186 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x187 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x188 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x189 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x18a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x18b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x18c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x18e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x190 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x191 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x192 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x193 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x194 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x195 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x196 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x197 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x198 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x199 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x19a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x19b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x19c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x19d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x19e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x19f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1a5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1a6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1ad 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1b5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1b6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1b7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1b8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1b9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1ba  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1bc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1bd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1be  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1c0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1c1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1c2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c3  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1c7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1c8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1c9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1cc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1cd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1ce  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1cf  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1d2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1d5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1d6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1d7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1d8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1d9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1da  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1db  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1dc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1dd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1de  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1df  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1e0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1e7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1e9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ea  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1eb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1ec  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None

```

I know I keep coming back with stuff but any ideas gents?

EDIT: Turns out none of my steam games are working now. Please help me Ubuntu community.

---

### Post by Jenopo on 2014-07-10
UPDATE: Removed, upgraded, updated, managed to get them all running again, and the screen's still turning off during certain games. Any further contributions.

---

### Post by mastablasta on 2014-07-11
it turns off?

is this a laptop?

does BIOS have any setting for power management?

---

### Post by Jenopo on 2014-07-11
Yeah this is a laptop, and yeah it's off, not illuminated, the computer is still running, I just have to force shutdown.

---

### Post by dannyboy79 on 2014-07-11
this is either a DPMS issue with your x server (it thinks it's not being used so it's going to sleep) or this is a pm-utils issue and your power management isn't setup properly. that's my 2 cents.

---

### Post by Jenopo on 2014-07-12
Ah right, so can I do something about that?

---

### Post by Jenopo on 2014-07-12
UPDATE 2: found another issue in the Kubuntu forums, it suggested turning off my power management settings (it's not quite the same issue), I did under system settings, still no joy. No idea if this is helping, but does that give anyone a clue as to where I should go next?

---

