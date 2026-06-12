---
title: "Ubuntu 12.04 LTS Unity is running in 2D mode instead of 3D. ATI Radeon 9200SE"
date: 2012-05-04
forum: Desktop Environments
---

### Post by altella on 2012-05-04
Hello all;

This is my first experience with Unity after my Ubuntu 10.04 LTS for the last two years.
I am trying to configure it, but when I run MyUnity program I obtain the  following message: "Ubuntu is running in 2D mode. Many Features will  not be available"
When executing "glxinfo" it appears that I have Direct Rendering in my ATI Radeon 9200. 
How can I correct this to have Unity 3D?

Thank you all in advance.

Attached the output og glxinfo:
alberto@alberto-desktop:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV280 5964)  TCL DRI2
OpenGL version string: 1.3 Mesa 8.0.2
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_SUN_multi_draw_arrays, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_EXT_framebuffer_object, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_occlusion_query, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_fragment_shader, GL_EXT_texture_cube_map, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_vertex_program, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_texture_rectangle, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_rectangle, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_texture_mirror_once, 
    GL_EXT_gpu_program_parameters, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_robustness

---

### Post by ajgreeny on 2012-05-04
That card with the open source driver is not capable of running 3D unity.  I have the same card on my desktop machine and it did not run unity in 3D in 11.10 either, so I have stuck with 10.04 at the moment, which incidentally I think is the best version of Ubuntu that there has been so far.

I do not like, and will not be using unity in any case, so will be trying the classic desktop version available for 12.04 by installing the **gnome-panel** package plus dependencies.  If that is still not to my taste, I will probably move to Xubuntu or Lubuntu, which can both be made to work just as I like my system to work.

---

### Post by altella on 2012-05-10
You are true, I have been testing the Xfce desktop and it is simply what I want. It works, It is fast, configurable and for me, much more usable.
My desktop was Gnome 2, and I think Unity, Gonme 3 or Gonme Shell are not going in the right direction. I do not like them and I realize there are a lot of people that dont like them either.
For now on Xfce will be my desktop....

---

