---
title: "Slow desktop in 10.04 with nvidia 195.36.24"
date: 2010-05-30
forum: Desktop Environments
---

### Post by gizmocan on 2010-05-30
I have a Zotac IONITX-F-E motherboard (Intel Atom Dual Core 1.6 GHz +  Nvidia ION) -based box with Ubuntu 10.04 64-bit installed.

With the nouveau driver, my desktop experience was smooth and great. However, I want to take advantage of the ION for playing 1080p video, so I removed nouveau.

After many hours, I finally got the Nvidia 195.36.24 drivers installed without errors. However, when I boot up, my desktop environment is very slow. For example, I click on a menu and the screen gets refreshed very slowly, requiring about a second before the menu is fully drawn.

I've found that if I leave the system inactive long enough for my display to get shut down by the power manager, the desktop will sometimes (very unpredictable) work normally upon resuming. Any ideas why this happens?

Any ideas on how to deal with this?

Thanks!

---

### Post by gizmocan on 2010-05-31
I just noticed that in the Hardware Drivers window, no drivers are listed and "No proprietary drivers are in use on this system." is displayed. However, as I stated above, I know I installed nvidia 195.36.24 and I had the installer modify the xorg.conf file.

So why doesn't my nvidia driver show up in the Hardware Drivers menu?

---

### Post by gizmocan on 2010-05-31
I don't know if this really counts as a solution, but I've gotten around the problem by going into System -> Preferences -> Appearance, then clicking on the Visual Effects tab and changing the option to None.

Now my desktop looks a little more boring, but it isn't slow!

---

### Post by doobiest on 2010-10-11
Thats totally not a solution and unfortunately I have the same problem with the same bored.  Did you ever find a fix to get proper acceleration?

---

### Post by vek on 2010-10-11
it honestly sounds like the driver isn't correctly working for you.
IF you run glxgears -info in a console it should dump your actual driver and should read something like nvidia 195.36.24 and not a software renderer.

Note that 10.10 should come with version 260.something, so unless you specifically opted not to install the driver, it might be that the old driver is preventing the new one from installing or something...

---

### Post by gizmocan on 2010-10-14
I upgraded to ubuntu 10.10, which helped me get 1080p video playback working using VLC, but it was no help with desktop effects.

If anyone has a fix for this, I'd love to hear about it.

---

### Post by vek on 2010-10-15
Can you verify that the nvidia driver is installed and working?

"glxgears -info" in a terminal might help... or just the jockey UI...

---

### Post by gizmocan on 2010-10-17
glxgears -info yielded:

```
GL_RENDERER   = ION/PCI/SSE2
GL_VERSION    = 3.3.0 NVIDIA 260.19.06
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
9480 frames in 5.0 seconds = 1895.896 FPS
9301 frames in 5.0 seconds = 1860.056 FPS
8205 frames in 5.0 seconds = 1640.962 FPS
9658 frames in 5.0 seconds = 1931.543 FPS
9070 frames in 5.0 seconds = 1813.956 FPS
8971 frames in 5.0 seconds = 1794.008 FPS
7960 frames in 5.0 seconds = 1591.944 FPS
```

The animated gears appeared and turned nicely and quickly. Does this help?

---

### Post by dado483 on 2011-01-03
Hi, i'm a little OT but i try to ask you...

I've also a Zotac IONITX F-E running ubuntu 10.04.

Are you able to shutdown?
When i try to shutdown, the system begin the shutdown procedure, but at the end the fan in the motherboard continue run and PC stays on.

I've opened a topic ([http://ubuntuforums.org/showthread.php?t=1477962](http://ubuntuforums.org/showthread.php?t=1477962)) but i've not received answers....

Thanks a lot!
Davide

---

### Post by gizmocan on 2011-01-11
I have never had any problems shutting down my computer.

I've since upgraded to 10.10 (which I found to be necessary to get 1080p video working correctly) and I can still shut down correctly.

---

