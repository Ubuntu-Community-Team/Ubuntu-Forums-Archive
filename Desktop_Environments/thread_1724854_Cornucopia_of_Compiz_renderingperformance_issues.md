---
title: "Cornucopia of Compiz rendering/performance issues"
date: 2011-04-08
forum: Desktop Environments
---

### Post by Eevee on 2011-04-08
Compiz just doesn't seem to want to get along with my machine, and I'm at my wit's end.  I've had a colorful rainbow of problems:

[list]
[*]Various graphical corruption, showing either repeating blocks of static or bits of junk from other windows.  I've seen this in windows I just maximized, as well as in the icons and previews in the (non-static) window switcher.  Also seen in some non-maximized windows, often terminals, where the entire window and its decorations are replaced with a rectangle of garbage, though the garbage still wobbles when moved if wobbly windows is enabled.
[*]When my screen is blanked and locked, there's a delay of up to a minute after moving the mouse or pressing a key before the "unlock" dialog renders.  After entering my password, there's another (shorter, but still quite noticeable) delay before the desktop redraws.  Sometimes the screen displays static garbage during this second delay.  Lately I've seen the blank screen sometimes render as garbage from the get-go.
[*]Performance generally degrades over time.  Compiz is *sometimes* quite snappy immediately after a boot and for a few days afterwards, but before long it becomes noticeably slow when switching workspaces or unmaximizing windows, usually pegging a core while it does so.  As of late this degredation has been on the order of several hours, rather than several days.
[*]Some graphical programs will, intermittently, scroll very badly.  Doesn't matter if I'm using the mouse wheel, arrow keys, pgup/pgdn.  X will lock up for several minutes while the window tries to scroll, pegged at 100 cpu the whole time.  It seems this is only caused by accelerated programs: Firefox, Evince, OpenOffice.org, and terminals are the major victims, but it can affect one of them without affecting the others (yet).  Restarting Compiz fixes the problem temporarily, restoring sane scrolling speed, but it generally recurs within a few hours unless I reboot.  What really baffles me is that software rendering should still handle PDF scrolling reasonably, so I have no idea what's going on here.
[*]At different times, gvim windows will scroll incorrectly; the effect is as if the new view had a transparent background and were painted directly on top of the old view.  It's no slower than usual; just results in a lot of junk accumulating.[/list]

There's no obvious sequence of events that causes—or fixes—any of the above, and a dozen attempts at googling have turned up nothing that sounds similar.  Because the problems only manifest sometimes, and only after some arbitrary trigger or amount of uptime, it's hard to tell what's helpful.  I don't do anything particularly stressful to my video card; occasional videos, and whatever applications are 2D-accelerated.  I've played a few 3D games in wine with reasonable performance when Compiz is disabled, and I've done a stress test on the video ram, so I doubt the hardware or drivers are outright broken.

Setup:
- Ubuntu 10.10; started around 8.04 and upgraded every release, until a clean reinstall of 10.10, though I kept a lot of config in ~.
- 8800 GTS using the proprietary nvidia driver.  Currently using 260.19.06.
- Two 1680×1050 monitors, using nvidia's TwinView.
- Compiz 0.8.6 atop X 1.9.0, default plugin set plus ADD Helper, Window Previews, and the non-static app switcher.
- 2×2 grid of workspaces using the wall; no cube or anything else 3D.
- Rarely run anything graphical outside Firefox (4), Thunderbird, Pidgin, Deluge, gvim, and a stack of roxterms.

I've tried all combinations of indirect-rendering and loose-binding, but none seem to make much difference.  I've tried resetting Compiz's configuration+plugins to their defaults, to no avail.  I tried upgrading the nvidia drivers, and got brief X freezes every few minutes.  On the Compiz recommendation, I tried switching to nouveau, and got X *hangs* due to some ancient known problem after a couple days.  The nouveau recommendation?  Don't use nouveau, or at least not with acceleration.  Awesome.


Here are some logs, though I doubt they'll be too helpful.  I last booted this morning (after downgrading from 270.x nvidia drivers, which made life worse), and since then have experienced a window decorator crash, several rounds of graphical corruption, and the insanely-slow-scrolling phenomenon.

Compiz rarely outright crashes, so no help there.

glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 260.19.06
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_buffer_unified_memory, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x041 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x042 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x044 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x045 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x046 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x048 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x049 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x04a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x054 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x056 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x05f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x060 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x063 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x064 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x065 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x067 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x068 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x069 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06a 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x070 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x071 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x072 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon

164 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ca  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cc  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cd  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0ce  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0cf  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0d0  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0d1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d2  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d4  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d5  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d6  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d7  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d8  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d9  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0da  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0db  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dc  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0de  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0df  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e0  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e2  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e4  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e5  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e6  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e7  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e8  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e9  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ea  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0eb  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ec  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ed  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ee  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ef  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f0  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f1  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f2  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f3  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f4  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f5  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f6  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f7  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f8  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f9  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fa  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fb  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fc  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0fe  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0ff  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x100  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x102  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x103  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x104  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10a  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10b  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10c  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10e  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10f  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x110  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x112  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x113  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x118  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
```

Xorg.0.log (not sure which of the errors match to which experiences, but I'm sure at least some of the problems didn't log anything)
```
[    25.977] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    25.977] X Protocol Version 11, Revision 0
[    25.977] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    25.977] Current Operating System: Linux tekkanin 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
[    25.977] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=314cc897-01fa-49da-a85a-08d5aa813362 ro quiet splash
[    25.977] Build Date: 09 January 2011  12:14:27PM
[    25.977] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    25.977] Current version of pixman: 0.18.4
[    25.977] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    25.977] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.977] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  8 08:17:16 2011
[    26.004] (==) Using config file: "/etc/X11/xorg.conf"
[    26.004] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.309] (==) No Layout section.  Using the first Screen section.
[    26.309] (**) |-->Screen "Screen0" (0)
[    26.309] (**) |   |-->Monitor "<default monitor>"
[    26.330] (**) |   |-->Device "Default Device"
[    26.330] (==) No monitor specified for screen "Screen0".
	Using a default monitor configuration.
[    26.330] (==) Automatically adding devices
[    26.330] (==) Automatically enabling devices
[    26.640] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.640] 	Entry deleted from font path.
[    26.822] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.822] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.822] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.822] (II) Loader magic: 0x7d17a0
[    26.822] (II) Module ABI versions:
[    26.822] 	X.Org ANSI C Emulation: 0.4
[    26.822] 	X.Org Video Driver: 8.0
[    26.822] 	X.Org XInput driver : 11.0
[    26.822] 	X.Org Server Extension : 4.0
[    26.823] (--) PCI:*(0:1:0:0) 10de:0193:10de:0420 rev 162, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[    26.823] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.823] (II) "extmod" will be loaded by default.
[    26.823] (II) "dbe" will be loaded by default.
[    26.823] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    26.823] (II) "record" will be loaded by default.
[    26.823] (II) "dri" will be loaded by default.
[    26.823] (II) "dri2" will be loaded by default.
[    26.823] (II) LoadModule: "glx"
[    26.902] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    29.082] (II) Module glx: vendor="NVIDIA Corporation"
[    29.102] 	compiled for 4.0.2, module version = 1.0.0
[    29.102] 	Module class: X.Org Server Extension
[    29.102] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    29.102] (II) Loading extension GLX
[    29.102] (II) LoadModule: "extmod"
[    29.322] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.384] (II) Module extmod: vendor="X.Org Foundation"
[    29.384] 	compiled for 1.9.0, module version = 1.0.0
[    29.384] 	Module class: X.Org Server Extension
[    29.384] 	ABI class: X.Org Server Extension, version 4.0
[    29.384] (II) Loading extension MIT-SCREEN-SAVER
[    29.384] (II) Loading extension XFree86-VidModeExtension
[    29.384] (II) Loading extension XFree86-DGA
[    29.384] (II) Loading extension DPMS
[    29.384] (II) Loading extension XVideo
[    29.384] (II) Loading extension XVideo-MotionCompensation
[    29.384] (II) Loading extension X-Resource
[    29.384] (II) LoadModule: "dbe"
[    29.384] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.393] (II) Module dbe: vendor="X.Org Foundation"
[    29.393] 	compiled for 1.9.0, module version = 1.0.0
[    29.393] 	Module class: X.Org Server Extension
[    29.393] 	ABI class: X.Org Server Extension, version 4.0
[    29.393] (II) Loading extension DOUBLE-BUFFER
[    29.393] (II) LoadModule: "record"
[    29.393] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.394] (II) Module record: vendor="X.Org Foundation"
[    29.394] 	compiled for 1.9.0, module version = 1.13.0
[    29.394] 	Module class: X.Org Server Extension
[    29.394] 	ABI class: X.Org Server Extension, version 4.0
[    29.394] (II) Loading extension RECORD
[    29.394] (II) LoadModule: "dri"
[    29.394] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.401] (II) Module dri: vendor="X.Org Foundation"
[    29.401] 	compiled for 1.9.0, module version = 1.0.0
[    29.401] 	ABI class: X.Org Server Extension, version 4.0
[    29.401] (II) Loading extension XFree86-DRI
[    29.401] (II) LoadModule: "dri2"
[    29.402] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.407] (II) Module dri2: vendor="X.Org Foundation"
[    29.407] 	compiled for 1.9.0, module version = 1.2.0
[    29.407] 	ABI class: X.Org Server Extension, version 4.0
[    29.407] (II) Loading extension DRI2
[    29.407] (II) LoadModule: "nvidia"
[    29.407] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    29.602] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.637] 	compiled for 4.0.2, module version = 1.0.0
[    29.637] 	Module class: X.Org Video Driver
[    29.713] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    29.713] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    29.713] (++) using VT number 7

[    29.739] (II) Loading sub module "fb"
[    29.739] (II) LoadModule: "fb"
[    30.106] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.185] (II) Module fb: vendor="X.Org Foundation"
[    30.185] 	compiled for 1.9.0, module version = 1.0.0
[    30.185] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.185] (II) Loading sub module "wfb"
[    30.185] (II) LoadModule: "wfb"
[    30.259] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.299] (II) Module wfb: vendor="X.Org Foundation"
[    30.299] 	compiled for 1.9.0, module version = 1.0.0
[    30.299] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.299] (II) Loading sub module "ramdac"
[    30.299] (II) LoadModule: "ramdac"
[    30.299] (II) Module "ramdac" already built-in
[    30.335] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.335] (==) NVIDIA(0): RGB weight 888
[    30.336] (==) NVIDIA(0): Default visual is TrueColor
[    30.336] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.336] (**) NVIDIA(0): Option "NoLogo" "True"
[    30.336] (**) NVIDIA(0): Option "TwinView" "1"
[    30.336] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
[    30.336] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
[    30.350] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.350] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.350] (II) NVIDIA(0):     enabled.
[    31.569] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:1:0:0 (GPU-0)
[    31.569] (--) NVIDIA(0): Memory: 327680 kBytes
[    31.569] (--) NVIDIA(0): VideoBIOS: 60.80.18.00.01
[    31.569] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.569] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.569] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:1:0:0
[    31.569] (--) NVIDIA(0):     DELL E228WFP (DFP-0)
[    31.569] (--) NVIDIA(0):     DELL E228WFP (DFP-1)
[    31.569] (--) NVIDIA(0): DELL E228WFP (DFP-0): 330.0 MHz maximum pixel clock
[    31.569] (--) NVIDIA(0): DELL E228WFP (DFP-0): Internal Dual Link TMDS
[    31.569] (--) NVIDIA(0): DELL E228WFP (DFP-1): 330.0 MHz maximum pixel clock
[    31.569] (--) NVIDIA(0): DELL E228WFP (DFP-1): Internal Dual Link TMDS
[    31.571] (**) NVIDIA(0): TwinView enabled
[    31.571] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[    31.604] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[    31.604] (II) NVIDIA(0): Validated modes:
[    31.604] (II) NVIDIA(0):    
[    31.604] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1680+0,DFP-1:nvidia-auto-select+0+0"
[    31.604] (II) NVIDIA(0): Virtual screen size determined to be 3360 x 1050
[    31.625] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[    31.625] (--) NVIDIA(0):     option
[    31.625] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    31.625] (--) Depth 24 pixmap format is 32 bpp
[    31.625] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.626] (II) NVIDIA(0): Initialized GPU GART.
[    31.630] (II) NVIDIA(0): Setting mode
[    31.630] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1680+0,DFP-1:nvidia-auto-select+0+0"
[    31.725] (II) Loading extension NV-GLX
[    31.819] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    31.865] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.865] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    31.865] (==) NVIDIA(0): Backing store disabled
[    31.865] (==) NVIDIA(0): Silken mouse enabled
[    31.899] (==) NVIDIA(0): DPMS enabled
[    31.899] (II) Loading extension NV-CONTROL
[    31.899] (II) Loading extension XINERAMA
[    31.899] (II) Loading sub module "dri2"
[    31.899] (II) LoadModule: "dri2"
[    31.900] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.900] (II) NVIDIA(0): [DRI2] Setup complete
[    31.900] (==) RandR enabled
[    31.900] (II) Initializing built-in extension Generic Event Extension
[    31.900] (II) Initializing built-in extension SHAPE
[    31.900] (II) Initializing built-in extension MIT-SHM
[    31.900] (II) Initializing built-in extension XInputExtension
[    31.900] (II) Initializing built-in extension XTEST
[    31.900] (II) Initializing built-in extension BIG-REQUESTS
[    31.900] (II) Initializing built-in extension SYNC
[    31.900] (II) Initializing built-in extension XKEYBOARD
[    31.900] (II) Initializing built-in extension XC-MISC
[    31.900] (II) Initializing built-in extension SECURITY
[    31.900] (II) Initializing built-in extension XINERAMA
[    31.900] (II) Initializing built-in extension XFIXES
[    31.900] (II) Initializing built-in extension RENDER
[    31.900] (II) Initializing built-in extension RANDR
[    31.900] (II) Initializing built-in extension COMPOSITE
[    31.900] (II) Initializing built-in extension DAMAGE
[    31.900] (II) Initializing built-in extension GESTURE
[    31.900] (II) Initializing extension GLX
[    32.816] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.841] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.841] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.841] (II) LoadModule: "evdev"
[    32.841] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.968] (II) Module evdev: vendor="X.Org Foundation"
[    32.968] 	compiled for 1.9.0, module version = 2.3.2
[    32.968] 	Module class: X.Org XInput Driver
[    32.968] 	ABI class: X.Org XInput driver, version 11.0
[    32.968] (**) Power Button: always reports core events
[    32.968] (**) Power Button: Device: "/dev/input/event1"
[    32.992] (II) Power Button: Found keys
[    32.992] (II) Power Button: Configuring as keyboard
[    32.992] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.992] (**) Option "xkb_rules" "evdev"
[    32.992] (**) Option "xkb_model" "pc105"
[    32.992] (**) Option "xkb_layout" "us"
[    32.995] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    32.995] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.995] (**) Power Button: always reports core events
[    32.995] (**) Power Button: Device: "/dev/input/event0"
[    33.032] (II) Power Button: Found keys
[    33.032] (II) Power Button: Configuring as keyboard
[    33.032] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.032] (**) Option "xkb_rules" "evdev"
[    33.032] (**) Option "xkb_model" "pc105"
[    33.032] (**) Option "xkb_layout" "us"
[    33.033] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event2)
[    33.033] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.033] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    33.033] (**) Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event2"
[    33.060] (II) Logitech Logitech Illuminated Keyboard: Found keys
[    33.060] (II) Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    33.060] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD)
[    33.060] (**) Option "xkb_rules" "evdev"
[    33.060] (**) Option "xkb_model" "pc105"
[    33.060] (**) Option "xkb_layout" "us"
[    33.060] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event3)
[    33.060] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.060] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    33.060] (**) Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event3"
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Found relative axes
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Found absolute axes
[    33.100] (II) evdev-grail: failed to open grail, no gesture support
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Found keys
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Configuring as mouse
[    33.100] (II) Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    33.100] (**) Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[    33.100] (**) Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.100] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD)
[    33.100] (**) Option "xkb_rules" "evdev"
[    33.100] (**) Option "xkb_model" "pc105"
[    33.100] (**) Option "xkb_layout" "us"
[    33.100] (EE) Logitech Logitech Illuminated Keyboard: failed to initialize for relative axes.
[    33.100] (II) Logitech Logitech Illuminated Keyboard: initialized for absolute axes.
[    33.101] (II) config/udev: Adding input device Razer Razer Diamondback 3G (/dev/input/event4)
[    33.101] (**) Razer Razer Diamondback 3G: Applying InputClass "evdev pointer catchall"
[    33.101] (**) Razer Razer Diamondback 3G: always reports core events
[    33.101] (**) Razer Razer Diamondback 3G: Device: "/dev/input/event4"
[    33.130] (II) Razer Razer Diamondback 3G: Found 11 mouse buttons
[    33.130] (II) Razer Razer Diamondback 3G: Found scroll wheel(s)
[    33.130] (II) Razer Razer Diamondback 3G: Found relative axes
[    33.130] (II) Razer Razer Diamondback 3G: Found x and y relative axes
[    33.130] (II) Razer Razer Diamondback 3G: Configuring as mouse
[    33.130] (**) Razer Razer Diamondback 3G: YAxisMapping: buttons 4 and 5
[    33.130] (**) Razer Razer Diamondback 3G: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.130] (II) XINPUT: Adding extended input device "Razer Razer Diamondback 3G" (type: MOUSE)
[    33.130] (II) Razer Razer Diamondback 3G: initialized for relative axes.
[    33.130] (II) config/udev: Adding input device Razer Razer Diamondback 3G (/dev/input/mouse0)
[    33.130] (II) No input driver/identifier specified (ignoring)
[ 13661.892] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[ 13661.892] 
Backtrace:
[ 13661.907] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[ 13661.907] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x458ea4]
[ 13661.907] 2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x488d74]
[ 13661.907] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f48e6e3f000+0x5319) [0x7f48e6e44319]
[ 13661.907] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f48e6e3f000+0x5a0e) [0x7f48e6e44a0e]
[ 13661.907] 5: /usr/bin/X (0x400000+0x6d4e7) [0x46d4e7]
[ 13661.907] 6: /usr/bin/X (0x400000+0x1161a3) [0x5161a3]
[ 13661.907] 7: /lib/libpthread.so.0 (0x7f48ecfe2000+0xfb40) [0x7f48ecff1b40]
[ 13661.907] 8: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f48e795a000+0xc8eb8) [0x7f48e7a22eb8]
[ 13661.907] 9: /usr/lib/xorg/modules/libwfb.so (wfbBlt+0x136) [0x7f48e7520766]
[ 13661.907] 10: /usr/lib/xorg/modules/libwfb.so (wfbCopyNtoN+0x2bf) [0x7f48e752521f]
[ 13661.907] 11: /usr/bin/X (miCopyRegion+0xa5) [0x55c2a5]
[ 13661.907] 12: /usr/bin/X (miDoCopy+0x43a) [0x55c93a]
[ 13661.907] 13: /usr/lib/xorg/modules/libwfb.so (wfbCopyArea+0x4c) [0x7f48e752463c]
[ 13661.907] 14: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f48e795a000+0x3e8702) [0x7f48e7d42702]
[ 13661.907] 15: /usr/bin/X (0x400000+0xdf664) [0x4df664]
[ 13661.907] 16: /usr/bin/X (0x400000+0x3e599) [0x43e599]
[ 13661.907] 17: /usr/bin/X (0x400000+0x3f979) [0x43f979]
[ 13661.907] 18: /usr/bin/X (0x400000+0x2187b) [0x42187b]
[ 13661.907] 19: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f48ebf4dd8e]
[ 13661.907] 20: /usr/bin/X (0x400000+0x21409) [0x421409]
[ 19853.364] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[ 19853.364] 
Backtrace:
[ 19853.380] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[ 19853.380] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x458ea4]
[ 19853.380] 2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x488d74]
[ 19853.380] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f48e6e3f000+0x5319) [0x7f48e6e44319]
[ 19853.380] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f48e6e3f000+0x5a0e) [0x7f48e6e44a0e]
[ 19853.380] 5: /usr/bin/X (0x400000+0x6d4e7) [0x46d4e7]
[ 19853.380] 6: /usr/bin/X (0x400000+0x1161a3) [0x5161a3]
[ 19853.380] 7: /lib/libpthread.so.0 (0x7f48ecfe2000+0xfb40) [0x7f48ecff1b40]
[ 19853.380] 8: /lib/libc.so.6 (nanosleep+0x10) [0x7f48ebfd91f0]
[ 19853.380] 9: /lib/libc.so.6 (usleep+0x34) [0x7f48ec00eb14]
[ 19853.380] 10: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f48e795a000+0x39c53c) [0x7f48e7cf653c]
[ 19853.380] 11: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f48e795a000+0x39c7b5) [0x7f48e7cf67b5]
[ 19853.380] 12: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f48e795a000+0x3b40f6) [0x7f48e7d0e0f6]
[ 19853.380] 13: /usr/lib/xorg/extra-modules/libglx.so (0x7f48eab58000+0x390b91) [0x7f48eaee8b91]
[ 20168.897] (EE) GLX encountered an error processing indirect rendering
[ 20168.897] (EE)    for client 35, which will now be closed.
[ 20168.897] (EE) Client exception raised, closing.
[ 20192.802] (EE) GLX encountered an error processing indirect rendering
[ 20192.802] (EE)    for client 21, which will now be closed.
[ 20192.802] (EE) Client exception raised, closing.
```

xorg.conf
```
Section "Screen"
	Identifier     "Screen0"
	Device         "Default Device"
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "DFP-1"
	Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load    "glx"
EndSection

Section "Device"
	Identifier      "Default Device"
	VendorName      "NVIDIA Corporation"
	BoardName       "GeForce 8800 GTS"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```


$ for file in $(find .gconf/apps/compiz/ -type f -size +1c); do echo --- $file; cat $file; echo; done
```
--- .gconf/apps/compiz/general/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="lower_window_button" mtime="1302277864" type="string">
		<stringvalue>&lt;Alt&gt;Button8</stringvalue>
	</entry>
	<entry name="toggle_window_maximized_button" mtime="1302277869" type="string">
		<stringvalue>&lt;Alt&gt;Button9</stringvalue>
	</entry>
	<entry name="cursor_size" mtime="1302296000" type="int" value="24"/>
	<entry name="cursor_theme" mtime="1302296000" type="string">
		<stringvalue>DMZ-White</stringvalue>
	</entry>
	<entry name="active_plugins" mtime="1301930173" type="list" ltype="string">
		<li type="string">
			<stringvalue>core</stringvalue>
		</li>
		<li type="string">
			<stringvalue>ccp</stringvalue>
		</li>
		<li type="string">
			<stringvalue>move</stringvalue>
		</li>
		<li type="string">
			<stringvalue>resize</stringvalue>
		</li>
		<li type="string">
			<stringvalue>place</stringvalue>
		</li>
		<li type="string">
			<stringvalue>decoration</stringvalue>
		</li>
		<li type="string">
			<stringvalue>addhelper</stringvalue>
		</li>
		<li type="string">
			<stringvalue>commands</stringvalue>
		</li>
		<li type="string">
			<stringvalue>dbus</stringvalue>
		</li>
		<li type="string">
			<stringvalue>extrawm</stringvalue>
		</li>
		<li type="string">
			<stringvalue>gnomecompat</stringvalue>
		</li>
		<li type="string">
			<stringvalue>grid</stringvalue>
		</li>
		<li type="string">
			<stringvalue>imgjpeg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>mousepoll</stringvalue>
		</li>
		<li type="string">
			<stringvalue>neg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>png</stringvalue>
		</li>
		<li type="string">
			<stringvalue>regex</stringvalue>
		</li>
		<li type="string">
			<stringvalue>resizeinfo</stringvalue>
		</li>
		<li type="string">
			<stringvalue>session</stringvalue>
		</li>
		<li type="string">
			<stringvalue>svg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>text</stringvalue>
		</li>
		<li type="string">
			<stringvalue>thumbnail</stringvalue>
		</li>
		<li type="string">
			<stringvalue>vpswitch</stringvalue>
		</li>
		<li type="string">
			<stringvalue>workarounds</stringvalue>
		</li>
		<li type="string">
			<stringvalue>wall</stringvalue>
		</li>
		<li type="string">
			<stringvalue>wobbly</stringvalue>
		</li>
		<li type="string">
			<stringvalue>animation</stringvalue>
		</li>
		<li type="string">
			<stringvalue>expo</stringvalue>
		</li>
		<li type="string">
			<stringvalue>ezoom</stringvalue>
		</li>
		<li type="string">
			<stringvalue>scale</stringvalue>
		</li>
		<li type="string">
			<stringvalue>scaleaddon</stringvalue>
		</li>
		<li type="string">
			<stringvalue>switcher</stringvalue>
		</li>
	</entry>
	<entry name="run_command_terminal_key" mtime="1217977873" type="string">
		<stringvalue>&lt;Mod4&gt;&lt;Hyper&gt;s</stringvalue>
	</entry>
	<entry name="toggle_window_shaded_key" mtime="1217977873" type="string">
		<stringvalue>Disabled</stringvalue>
	</entry>
	<entry name="run_command0_key" mtime="1217977873" type="string">
		<stringvalue>&lt;Mod4&gt;&lt;Hyper&gt;e</stringvalue>
	</entry>
	<entry name="command0" mtime="1217977873" type="string">
		<stringvalue>nautilus ~</stringvalue>
	</entry>
	<entry name="autoraise_delay" mtime="1217977873" type="int" value="500"/>
	<entry name="autoraise" mtime="1217977873" type="bool" value="false"/>
	<entry name="abi" mtime="1217977873" type="int" value="20080401"/>
</gconf>

--- .gconf/apps/compiz/general/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="force_independent_output_painting" mtime="1301363046" type="bool" value="true"/>
	<entry name="refresh_rate" mtime="1302277771" type="int" value="60"/>
	<entry name="detect_refresh_rate" mtime="1301331817" type="bool" value="false"/>
	<entry name="focus_prevention_level" mtime="1300988900" type="int" value="0"/>
	<entry name="vsize" mtime="1300378901" type="int" value="2"/>
	<entry name="hsize" mtime="1300378900" type="int" value="2"/>
	<entry name="texture_compression" mtime="1211510379" type="bool" value="false"/>
</gconf>

--- .gconf/apps/compiz/plugins/animation/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="fire_life" mtime="1229837995" type="float" value="0.40000000596046448"/>
	<entry name="fire_particles" mtime="1229837995" type="int" value="1600"/>
	<entry name="fire_slowdown" mtime="1229837995" type="float" value="0.3345000147819519"/>
	<entry name="fire_size" mtime="1229837995" type="float" value="3"/>
	<entry name="domino_direction" mtime="1229837995" type="int" value="1"/>
	<entry name="fold_gridx" mtime="1229837995" type="int" value="1"/>
	<entry name="fire_color" mtime="1229837995" type="string">
		<stringvalue>#ddbf7cff</stringvalue>
	</entry>
</gconf>

--- .gconf/apps/compiz/plugins/water/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="initiate_button" mtime="1205110624" type="string">
                <stringvalue>Button0</stringvalue>
        </entry>
        <entry name="initiate_edgebutton" mtime="1205110624" type="int" value="0">
        </entry>
        <entry name="initiate_bell" mtime="1205110624" type="bool" value="false">
        </entry>
        <entry name="initiate_edge" mtime="1205110624" type="list" ltype="string">
        </entry>
</gconf>

--- .gconf/apps/compiz/plugins/wobbly/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="snap_inverted" mtime="1230088513" type="bool" value="false">
        </entry>
        <entry name="snap_button" mtime="1205299951" type="string">
                <stringvalue>Button0</stringvalue>
        </entry>
        <entry name="snap_edgebutton" mtime="1205299951" type="int" value="0">
        </entry>
        <entry name="snap_bell" mtime="1205299951" type="bool" value="false">
        </entry>
        <entry name="snap_edge" mtime="1205299951" type="list" ltype="string">
        </entry>
</gconf>

--- .gconf/apps/compiz/plugins/wobbly/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="maximize_effect" mtime="1302277936" type="bool" value="false"/>
</gconf>

--- .gconf/apps/compiz/plugins/addhelper/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="window_types" mtime="1301063202" type="string">
		<stringvalue>(Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal) &amp; !(name=totem)</stringvalue>
	</entry>
	<entry name="saturation" mtime="1300999944" type="int" value="40"/>
	<entry name="brightness" mtime="1300999953" type="int" value="80"/>
	<entry name="ononinit" mtime="1300999921" type="bool" value="true"/>
	<entry name="toggle_button" mtime="1205297377" type="string">
		<stringvalue>Button0</stringvalue>
	</entry>
	<entry name="toggle_edgebutton" mtime="1205297377" type="int" value="0"/>
	<entry name="toggle_bell" mtime="1205297377" type="bool" value="false"/>
	<entry name="toggle_edge" mtime="1205297377" type="list" ltype="string">
	</entry>
</gconf>

--- .gconf/apps/compiz/plugins/expo/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="hide_docks" mtime="1239851575" type="bool" value="false"/>
	<entry name="expo_button" mtime="1205299951" type="string">
		<stringvalue>Button0</stringvalue>
	</entry>
	<entry name="expo_edgebutton" mtime="1205299951" type="int" value="0"/>
	<entry name="expo_bell" mtime="1205299951" type="bool" value="false"/>
</gconf>

--- .gconf/apps/compiz/plugins/scale/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="initiate_edgebutton" mtime="1205299951" type="int" value="0"/>
	<entry name="initiate_bell" mtime="1205299951" type="bool" value="false"/>
</gconf>

--- .gconf/apps/compiz/plugins/cubecaps/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="draw_bottom" mtime="1228419313" type="bool" value="false">
        </entry>
        <entry name="draw_top" mtime="1228419313" type="bool" value="false">
        </entry>
</gconf>

--- .gconf/apps/compiz/plugins/cube/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="backgrounds" mtime="1228419313" type="list" ltype="string">
		<li type="string">
			<stringvalue>/home/eevee/Pictures/00660_splash_1680x1050.jpg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>/home/eevee/Pictures/01232_lazydaysii_1680x1050.jpg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>/home/eevee/Pictures/01076_foggymorning2_1680x1050.jpg</stringvalue>
		</li>
		<li type="string">
			<stringvalue>/home/eevee/Pictures/00814_epicfalls_1680x1050.jpg</stringvalue>
		</li>
	</entry>
</gconf>

--- .gconf/apps/compiz/plugins/scalefilter/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="filter_case_insensitive" mtime="1239851575" type="bool" value="true"/>
</gconf>

--- .gconf/apps/compiz/plugins/workarounds/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="legacy_fullscreen" mtime="1301419267" type="bool" value="true"/>
	<entry name="convert_urgency" mtime="1300978703" type="bool" value="true"/>
	<entry name="force_glx_sync" mtime="1245049541" type="bool" value="true"/>
</gconf>

--- .gconf/apps/compiz/plugins/decoration/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="command" mtime="1301217568" type="string">
		<stringvalue>gtk-window-decorator --replace</stringvalue>
	</entry>
	<entry name="shadow_y_offset" mtime="1301217568" type="int" value="1"/>
	<entry name="shadow_radius" mtime="1301217568" type="float" value="4"/>
	<entry name="shadow_opacity" mtime="1301217568" type="float" value="0.59469997882843018"/>
</gconf>

--- .gconf/apps/compiz/plugins/thumbnail/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="fade_speed" mtime="1300978459" type="float" value="0.10000000149011612"/>
</gconf>

--- .gconf/apps/compiz/plugins/resizeinfo/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="always_show" mtime="1301063182" type="bool" value="true"/>
</gconf>

--- .gconf/apps/compiz/plugins/switcher/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="opacity" mtime="1301063182" type="int" value="80"/>
	<entry name="brightness" mtime="1301063182" type="int" value="60"/>
	<entry name="saturation" mtime="1301063182" type="int" value="60"/>
	<entry name="zoom" mtime="1301063182" type="float" value="0"/>
</gconf>

--- .gconf/apps/compiz/plugins/extrawm/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="activate_demands_attention_key" mtime="1300978540" type="string">
		<stringvalue>&lt;Super&gt;Tab</stringvalue>
	</entry>
</gconf>

--- .gconf/apps/compiz/plugins/fade/screen0/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="fade_mode" mtime="1300978639" type="int" value="1"/>
</gconf>

--- .gconf/apps/compiz/plugins/wall/allscreens/options/%gconf.xml
<?xml version="1.0"?>
<gconf>
	<entry name="edge_radius" mtime="1301930141" type="int" value="1"/>
</gconf>
```


Anything sound familiar, or anything else I can paste/try?  This has been going on intermittently for ages, but lately it's gotten so bad that I can't even run Compiz without risking scrolling freezes or window decoration crashes.  Kind of considering buying a more recent video card in the hopes that it plays better with the nvidia driver, or maybe just switching to xfce.

---

