---
title: "Compiz is buggy"
date: 2012-04-20
forum: Desktop Environments
---

### Post by snipe2004 on 2012-04-20
Hi,

As a short video will explain this better than any words...

[http://vimeo.com/40590116](http://vimeo.com/40590116)

EDIT : well, this one is closer from what I wanna show you : [https://vimeo.com/40721258](https://vimeo.com/40721258)

--> as you can see, using compiz is a real mess : that kind of black cloud on the screen (erasable using the mouse or another window), no animation on the title bar buttons, no refresh on the screen, invisible windows (until I pass the mouse over...),...

I'm praying you could help me... Here are the results of some commands that could, I hope, help you find the matter :

Glxinfo
```
arnault@arnault-laptop:~$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x209)
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
```
Compiz --replace
```
arnault@arnault-laptop:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing imgsvg options...done
Initializing gnomecompat options...done
compiz (core) - Error: Plugin 'text' not loaded.

compiz (ring) - Warn: No compatible text plugin loaded
Initializing ring options...done
Initializing session options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing animation options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing animationaddon options...done
Initializing scale options...done
Initializing showdesktop options...done
Setting Update "refresh_rate"
Setting Update "sync_to_vblank"
Setting Update "shadow_color"
Setting Update "command"
Setting Update "mipmap"
Setting Update "decoration_match"
Setting Update "run_key"
Setting Update "run_command_terminal_key"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "close_matches"
Setting Update "close_options"
Setting Update "minimize_effects"
Setting Update "minimize_durations"
Setting Update "minimize_matches"
Setting Update "friction"
Setting Update "spring_k"
Setting Update "fullscreen_visual_bell"
Setting Update "unresponsive_brightness"
Setting Update "unresponsive_saturation"
Setting Update "initiate_all_edge"
```
Glxspheres
```
arnault@arnault-laptop:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0xfc
Context is Direct
OpenGL Renderer: Gallium 0.4 on llvmpipe (LLVM 0x209)
8.061304 frames/sec - 8.996416 Mpixels/sec
7.739165 frames/sec - 8.636908 Mpixels/sec
8.243192 frames/sec - 9.199403 Mpixels/sec
8.186902 frames/sec - 9.136583 Mpixels/sec
7.723856 frames/sec - 8.619823 Mpixels/sec
7.434029 frames/sec - 8.296376 Mpixels/sec
6.965088 frames/sec - 7.773038 Mpixels/sec
6.357203 frames/sec - 7.094639 Mpixels/sec
7.243581 frames/sec - 8.083836 Mpixels/sec
7.766018 frames/sec - 8.666876 Mpixels/sec
6.987086 frames/sec - 7.797588 Mpixels/sec
7.135033 frames/sec - 7.962697 Mpixels/sec
6.945393 frames/sec - 7.751058 Mpixels/sec
7.303251 frames/sec - 8.150429 Mpixels/sec
6.807733 frames/sec - 7.597430 Mpixels/sec
6.933994 frames/sec - 7.738338 Mpixels/sec
7.710805 frames/sec - 8.605258 Mpixels/sec
```

Unity test:
```
arnault@arnault-laptop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x209)
OpenGL version string:  2.1 Mesa 8.0-rc2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

Glxgears -info
```
arnault@arnault-laptop:~$ glxgears -info
GL_RENDERER   = Gallium 0.4 on llvmpipe (LLVM 0x209)
GL_VERSION    = 2.1 Mesa 8.0-rc2
GL_VENDOR     = VMware, Inc.
GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_shader_texture_lod GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness GL_ARB_texture_storage
```

chipset
```
arnault@arnault-laptop:~$ grep Chipset /var/log/Xorg.0.log
[ 11206.886] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[ 11206.896] (II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
[ 11206.942] (II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
```

Compiz-check:
```
arnault@arnault-laptop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
nVidia Corporation Device 0de9 (rev a1)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) I
Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) n

```

Perhaps will you also find useful to know more about [my laptop](http://aldi.medion.com/md98921/be_fr/?refPage=medion) :
```
MEDION AKOYA P7624 (MD 98921)
Processeur Intel Core™ i5-2430M 2,40 GHz (Turbo Boost 2,0 jusqu‘à 3,0 GHz, 3 Mo Intel Smart Cache, Intel Hyper-Threading)
NVIDIA GeForce GT630M DirectX 11 (1024 Mo de mémoire, sortie numérique audio/vidéo HDMI et Optimus) + Intel Centrino Advanced-N 1030 (Bluetooth 3.0 intégré)
Ubuntu 11.04 Natty Narwhal + Windows 7 (Dual boot)
```-->I have Optimus, but I learned somewhere on the net that the visual effects of Compiz were managed by the Intel chipset... So I uninstalled everything about nVidia (including Bumblebee) and then Compiz started working - well, as you have seen, "working"...

Thanks for any help!!!

---

### Post by snipe2004 on 2012-04-20
Well, in fact I realize that when I "use" compiz (ex. : moving a window, closing another,...), it uses 75, 95 and up to 155 % of my CPU O_o

Is it normal ?

---

