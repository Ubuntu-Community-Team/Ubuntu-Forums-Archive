---
title: "Jaunty Intel 945GM graphics issues"
date: 2009-04-27
forum: General Help
---

### Post by oddworld on 2009-04-27
My graphics are really slow on my Dell laptop. 
Intel 945GM

```

davis@davis-laptop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
davis@davis-laptop:~$ glxgears
get fences failed: -1
param: 6, val: 0
852 frames in 5.0 seconds = 170.300 FPS
davis@davis-laptop:~$ glxgears -info
get fences failed: -1
param: 6, val: 0
GL_RENDERER   = Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.4
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
994 frames in 5.0 seconds = 198.640 FPS
^C
davis@davis-laptop:~$ 



```

---

### Post by huntzire on 2009-04-27
> **oddworld said:**
> My graphics are really slow on my Dell laptop. 
Intel 945GM

```

davis@davis-laptop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
davis@davis-laptop:~$ glxgears
get fences failed: -1
param: 6, val: 0
852 frames in 5.0 seconds = 170.300 FPS
davis@davis-laptop:~$ glxgears -info
get fences failed: -1
param: 6, val: 0
GL_RENDERER   = Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.4
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
994 frames in 5.0 seconds = 198.640 FPS
^C
davis@davis-laptop:~$ 



```

its slow on this guy's system too
[http://ubuntuforums.org/showthread.php?t=1138884](http://ubuntuforums.org/showthread.php?t=1138884)
still looking into it might submit bug report if we keep getting people with these issues.

---

### Post by stoneage on 2009-04-27
Don't really know what else to say except I hope this helps you some:-
[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=rcr&q=%22get+fences+failed%3A+-1%22+ubuntu+jaunty+9.04&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=rcr&q=%22get+fences+failed%3A+-1%22+ubuntu+jaunty+9.04&btnG=Search&meta=)

---

### Post by oddworld on 2009-04-27
I tried to revert back using this, but I cant figure out how to get the GPG key after adding the sources to sources.list

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by jaffa_nz on 2009-04-27
Kia Ora

To get the key is written clearly from a link on the page you mention.

here it is here
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

cheers

---

### Post by wispygalaxy on 2009-04-27
I use Intel 945GM, too.  It's slow in general.  :(

---

### Post by almikul on 2009-05-04
I tried to revert back to the Intrepid's driver, and it slightly improved the performance, but it is still quite slow. 

In 1280x800 mode in Intrepid, the glxgears gave me ~800 fps while the Jaunty gives me ~160 fps w/ EXA and ~350 fps w/ UXA. The problem is that UXA does not work when I increase the virtual resolution to connect the second monitor. Also, no matter if it's UXA or EXA, the flash in full screen mode is horrible. 

When I revert back to Intrepid's video driver in Jaunty, glxgears gives me around 250 fps, but the flash video is still very jerky.

---

### Post by It_was_me on 2009-05-05
> **jaffa_nz said:**
> Kia Ora

To get the key is written clearly from a link on the page you mention.

here it is here
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

cheers

I found this page about 2 weeks ago. The problem was finding the GPG key to add... I spent 5 days searching for his key. I noticed he updated his page very recently, with the command how to add his key...

---

