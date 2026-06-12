---
title: "Intel 945GM slow linux graphocs"
date: 2008-12-25
forum: General Help
---

### Post by oddworld on 2008-12-25
I have a feeling there is something wrong with my driver, Intel 945GM on the Dell e1405. Core 2 Duo CPU at 1.83 ghz, 2.0 Gigs of RAM.

I have been having problems especially with igoogle.com and youtube.
Sometimes navigating the file structure can be slow with nautilus.

I have added xubuntu (XFCE) and KDE to my ubuntu computer to see if it would make anything faster, KDE was incredibly slow, XFCE was pretty fast.
But no matter what I do, igoogle.com is always sluggish.
Is there something wrong? I used to get around 1,000 fps in glxgears

Now with 8.10 it is slower...
```

639 frames in 5.0 seconds = 127.784 FPS
647 frames in 5.0 seconds = 129.309 FPS

```

```


davis@davis-laptop:~$ glxgears -info
GL_RENDERER   = Software Rasterizer
GL_VERSION    = 2.1 Mesa 7.2
GL_VENDOR     = Mesa Project
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
639 frames in 5.0 seconds = 127.784 FPS
647 frames in 5.0 seconds = 129.309 FPS
^C
davis@davis-laptop:~$ 


```

---

### Post by igknighted on 2008-12-25
Did you do an upgrade?  Or a fresh install?

Granted I have a different card (gm45), but it appears you are not using the hardware for rendering.

GL_RENDER should be Mesa DRI
GL_VERSION should be 1.4 mesa 7.2
GL_VENDOR should be tungsten graphics, as they developed a lot of the new hardware acceleration code for the new intel driver (until GEM is ready)

I suspect an upgrade from an old version left old code on your system, but I can't be sure.  That said, your graphics card is definitely not rendering your desktop like it should, so I'm not surprised it is sluggish.

I'd try ```
sudo apt-get remove --purge xserver-xorg-video-intel libgl1* libdrm2
```, and then ```
sudo apt-get install xserver-xorg-video-intel libgl1-mesa-dri libgl1-mesa-glx
```

But if that doesn't work, it might take a fresh install.

---

### Post by oddworld on 2008-12-26
Well, I had a fresh copy of ubuntu 8.10, but after running:
```

sudo apt-get remove --purge xserver-xorg-video-intel libgl1* libdrm2

```
everything died.
I lost network manager, the mouse, basically everything.
So after losing the network, I could not reinstall the second line of code you mentioned.
I had to reformat. (no big deal, its not windows or anything :)

After being convinced 8.10 is sketchy, I went back to 8.04 but this time I decided to give 64bit a try.
Everything is back to normal, for some reason the default configuration does not work well on my laptop. 
I am back to getting ~1,000 fps on my laptop with 8.04

Any ideas why 8.10 was not working well? I had a fresh install.

```


davis@davis-laptop:~$ glxgears -info
GL_RENDERER   = Mesa DRI Intel(R) 945GM 20061017
GL_VERSION    = 1.3 Mesa 7.0.3-rc2
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
4745 frames in 5.0 seconds = 948.849 FPS



```

---

### Post by oddworld on 2008-12-26
Quick question:

> GL_VENDOR should be tungsten graphics, as they developed a lot of the new hardware acceleration code for the new intel driver (until GEM is ready)

What is GEM?

---

