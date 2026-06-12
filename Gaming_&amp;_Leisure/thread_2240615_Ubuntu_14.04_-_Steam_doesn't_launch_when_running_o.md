---
title: "Ubuntu 14.04 - Steam doesn't launch when running on nvidia GPU (nvidia-prime)"
date: 2014-08-21
forum: Gaming &amp; Leisure
---

### Post by Adam_Maris on 2014-08-21
Hello,

I have Ubuntu 14.04, kernel 3.13.0-34, x86_64. I have switchable graphics:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)

```

I use 331.38 driver (nvidia-331 package) with nvidia-prime. I have problem with running Steam on nvidia GPU, it simply won't start. On intel GPU Steam runs well. Here is the output:

```
$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1407966480_client)
Installing breakpad exception handler for appid(steam)/version(1407966480)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Process 4695 created /adam-ValveIPCSharedObjects5
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20140813141634)
Installing breakpad exception handler for appid(steamwebhelper)/version(1407939394)
[0821/105343:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20140813141634)
Installing breakpad exception handler for appid(steamwebhelper)/version(1407939394)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1407966480)
Installing breakpad exception handler for appid(steam)/version(1407966480)
Installing breakpad exception handler for appid(steam)/version(1407966480)
Installing breakpad exception handler for appid(steam)/version(1407966480)
Installing breakpad exception handler for appid(steam)/version(1407966480)
Generating new string page texture 7: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 8: 64x256, total string texture memory is 196,61 KB
Generating new string page texture 9: 48x256, total string texture memory is 245,76 KB
Generating new string page texture 10: 256x256, total string texture memory is 507,90 KB

```

And then nothing happens. When using intel GPU, the output is almost identical (a bit different order of some lines and line "Process 4695 created /adam-ValveIPCSharedObjects5" is missing) except that Steam launches fine. Here is some information about GPU:

```
$ glxinfo | grep "OpenGL"
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 630M/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 331.38
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.4.0 NVIDIA 331.38
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:

```

Do you know what could be the cause of this problem?

Thanks in advance.

---

### Post by oldrocker99 on 2014-08-21
Please post the output of
```
glxinfo
```

---

### Post by Adam_Maris on 2014-08-21
It's rather long, but as you wish. :)
```
$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_SGI_video_sync
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_copy_image, GLX_NV_float_buffer, GLX_NV_multisample_coverage, 
    GLX_NV_present_video, GLX_NV_swap_group, GLX_NV_video_capture, 
    GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 630M/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 331.38
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_multi_draw_indirect, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_compute_shader, GL_ARB_compute_variable_group_size, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_indirect_parameters, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_draw_parameters, GL_ARB_shader_group_vote, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_image_size, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sparse_texture, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_Cg_shader, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_blend_equation_advanced, GL_NV_blend_square, GL_NV_compute_program5, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_draw_texture, 
    GL_NV_explicit_multisample, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

OpenGL version string: 4.4.0 NVIDIA 331.38
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
    GL_AMD_multi_draw_indirect, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_compute_shader, 
    GL_ARB_compute_variable_group_size, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_indirect_parameters, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_query_buffer_object, GL_ARB_robust_buffer_access_behavior, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_draw_parameters, GL_ARB_shader_group_vote, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_image_size, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sparse_texture, 
    GL_ARB_stencil_texturing, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_buffer_range, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_Cg_shader, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_blend_equation_advanced, GL_NV_blend_square, GL_NV_compute_program5, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_draw_texture, 
    GL_NV_explicit_multisample, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

228 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x064 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x067 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x068 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x069 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x06a 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x06f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x070 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x071 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x072 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x074 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x076 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x078 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x079 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x07a 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x07c 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x07d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x07e 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x07f 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x080 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x081 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x082 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x083 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x084 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x085 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x086 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x087 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x088 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x089 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x08a 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x08b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x08c 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x08e 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x08f 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x090 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x092 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x094 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x095 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x098 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x09a 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09d 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x09e 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0a0 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a4 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0a6 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a8 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0aa 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0ac 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0ad 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0ae 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b0 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b1 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0b2 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b5 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b7 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0bb 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0bc 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0bd 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0c2 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0c3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c5 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0ca 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0cb 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0cc 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0cd 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0ce 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0cf 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d1 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0d2 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0d3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0d5 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0d6 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0d7 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0d8 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0d9 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0da 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0db 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0dc 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0dd 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0de 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0df 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e0 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e1 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e2 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0e4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x0e5 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e7 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x0e9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0ea 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0eb 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ec 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ed 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ee 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0ef 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f0 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x0f1 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f2 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f3 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x0f5 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0f6 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0f7 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x0f9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0fa 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0fb 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x0fc 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0fd 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0fe 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ff 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x100 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x101 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x102 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x103 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x104 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x105 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x106 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x107 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x108 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x109 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x10a 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x10b 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x10c 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x10d 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x10e 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x10f 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x110 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x111 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x112 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x113 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x114 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x115 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x116 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x117 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x118 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x119 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x11a 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x11b 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x11c 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x11d 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x11e 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x11f 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x120 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x121 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x122 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x123 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x124 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x125 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x126 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x127 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x128 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x129 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x12a 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x12b 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x12c 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x12d 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x12e 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x12f 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x130 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x131 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x132 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x133 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x134 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x135 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x136 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x137 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x138 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x139 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x13a 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x13b 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x13c 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x13d 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x13e 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x13f 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x140 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x141 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x142 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x143 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x144 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x145 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x146 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x147 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon

311 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x148 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x149 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x14a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x14b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x14c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x14d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x14e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x14f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x150 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x151 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x152 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x153 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x154 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x155 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x156 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x157 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x158 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x159 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x15a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x15b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x15c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x15d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x15e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x15f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x160 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x161 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x162 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x163 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x164 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x165 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x166 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x167 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x168 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x169 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x16a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x16b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x16c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x16d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x16e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x16f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x170 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x171 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x172 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x173 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x174 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x175 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x176 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x177 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x178 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x179 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x17a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x17b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x17c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x17d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x17e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x17f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x180 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x181 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x182 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x183 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x184 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x185 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x186 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x187 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x188 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x189 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x18a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x18b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x18c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x18d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x18e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x18f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x190 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x191 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x192 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x193 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x194 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x195 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x196 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x197 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x198 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x199 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x19a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x19b 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x19c 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x19d 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x19e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x19f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1a0 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1a1 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1a2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1a3 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1a4 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1a5 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1a6 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1a7 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1a8 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1a9 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1aa 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1ab 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1ac 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1ad 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1ae 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1af 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1b0 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b1 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b2 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b3 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b4 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b5 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b6 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b7 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1b8 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1b9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1ba 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1bb 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1bc 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1bd 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1be 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1bf 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c0 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c1 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c3 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c4 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c5 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c6 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c7 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x1c8 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1c9 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1ca 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1cb 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1cc 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1cd 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1ce 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1cf 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x1d0 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d1 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d3 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d4 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d5 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d6 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d7 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x1d8 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1d9 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1da 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1db 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1dc 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1dd 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1de 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1df 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x1e0 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x1e1 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x1e2 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x1e3 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x1e4 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x1e5 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x1e6 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x1e7 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x1e8 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x1e9 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x1ea 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x1eb 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x1ec 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1ed 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1ee 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1ef 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1f0 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1f1 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x1f2 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1f3 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x1f4 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1f5 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1f6 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1f7 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1f8 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1f9 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x1fa 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1fb 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x1fc 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1fd 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x1fe 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x1ff 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x200 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x201 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x202 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x203 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x204 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x205 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x206 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x207 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x208 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x209 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x20a 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x20b 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x20c 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x20d 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x20e 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x20f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x210 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x211 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x212 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x213 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  8 1 Ncon
0x214 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x215 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x216 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x217 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 16 1 Ncon
0x218 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x219 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x21a 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x21b 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x21c 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x21d 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x21e 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x21f 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  8 1 Ncon
0x220 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x221 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x222 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x223 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 16 1 Ncon
0x224 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x225 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x226 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x227 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16 32 1 Ncon
0x228 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x229 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x22a 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x22b 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16 32 1 Ncon
0x22c  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x22d  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x22e  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x22f  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x230  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x231  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x232  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x233  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x234  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x235  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x236  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x237  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x238  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x239  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23a  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23b  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23c  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23d  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23e  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x23f  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x240  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x241  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x242  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x243  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x244  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x245  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x246  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x247  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x248  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x249  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x24a  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x24b  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x24c  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x24d  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x24e  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x24f  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x250  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x251  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x252  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x253  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x254  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x255  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x256  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x257  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x258  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x259  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x25a  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x25b  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x25c  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x25d  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x25e  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x25f  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x260  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x261  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x262  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x263  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x264  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x265  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x266  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x267  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x268  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x269  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26a  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26b  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26c  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26d  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26e  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x26f  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x270  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x271  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x272  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x273  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x274  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x275  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x276  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x277  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x278  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x279  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x27a  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x27b  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x27c  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x27d  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x27e  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None


```

---

### Post by oldrocker99 on 2014-08-21
Hmmm...Nothing looks amiss in your glxinfo. You can try uninstalling and reinstalling Steam; it might or might not help.

---

### Post by Adam_Maris on 2014-08-21
Well, I tried and it didn't help. What would you recommend me to do next? Should I try to install new driver or use bumblebee instead of nvidia-prime? Or ask at steam forum at first?

Thanks.

---

### Post by oldrocker99 on 2014-08-21
The current nVidia driver is 3.43. If you haven't enabled the xorg-edgers PPA, which has the most up-to-date Ubuntu nVidia drivers, install it by typing or cutting and pasting: 
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-343
```

Hopefully, this will help.

---

### Post by ikki_72 on 2014-08-22
I had same issue too. Installing any driver besides nouveou will make my screen's resolution too wide and unable to change resolution because of it.

tested on asus pro45vj

---

### Post by Adam_Maris on 2014-08-24
Ikki's right. It widened my screen so it wasn't usable and I couldn't change the resolution. Maybe I can try some other nvidia driver versions and maybe some driver will work, however I don't see it very promising.

---

### Post by ikki_72 on 2014-09-22
so i removed nouveou
sudo apt-get remove xserver-xorg-video-nouveau

install nvidia-331.38

install bumblebee (optional)
sudo apt-get install git
mkdir git && cd git
git clone [https://github.com/Bumblebee-Project/bumblebee-ui.git](https://github.com/Bumblebee-Project/bumblebee-ui.git)
cd bumblebee-ui
sudo ./INSTALL

sudo apt-get install libgl1-mesa-glx:amd64 libgl1-mesa-glx:i386 libgl1-me
sa-dri:amd64 libgl1-mesa-dri:i386

then I can successfully load steam

---

