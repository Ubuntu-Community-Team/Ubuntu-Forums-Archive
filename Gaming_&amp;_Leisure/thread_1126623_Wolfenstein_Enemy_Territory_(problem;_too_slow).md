---
title: "Wolfenstein: Enemy Territory (problem; too slow)"
date: 2009-04-15
forum: Gaming &amp; Leisure
---

### Post by WolfETplayer on 2009-04-15
I followed the instructions from [here]("https://help.ubuntu.com/community/EnemyTerritory") and everything seemed to go smoothly up until I tried to create a profile... I found that I couldn't do this, because the game was working too slowly.  So, how do I fix this?  Please help.

```
desktop:~$ wget -c http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
--2009-04-15 13:07:10--  http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
Resolving ftp.games.skynet.be... 195.238.1.6
Connecting to ftp.games.skynet.be|195.238.1.6|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270965248 (258M) [text/plain]
Saving to: `et-linux-2.60.x86.run'

100%[======================================>] 270,965,248 60.6K/s   in 79m 8s  

2009-04-15 14:26:25 (55.7 KB/s) - `et-linux-2.60.x86.run' saved [270965248/270965248]

desktop:~$ wget -c http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60-update.x86.run
--2009-04-15 15:54:44--  http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60-update.x86.run
Resolving ftp.games.skynet.be... 195.238.1.6
Connecting to ftp.games.skynet.be|195.238.1.6|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8493622 (8.1M) [text/plain]
Saving to: `et-linux-2.60-update.x86.run'

100%[======================================>] 8,493,622   60.6K/s   in 2m 17s  

2009-04-15 15:57:02 (60.7 KB/s) - `et-linux-2.60-update.x86.run' saved [8493622/8493622]

desktop:~$ sudo sh ./et-linux-2.60.x86.run
[sudo] password for rl: 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
/home/rl/.setup6482: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

























 Enemy Territory 2.60 Installation
 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; 






              &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Request &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
              &#9474; Installation complete!                         &#9474;  
              &#9474; Would you like to start now?                   &#9474;  
              &#9474;                                                &#9474;  
              &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;  
              &#9474;             < Yes >       < No  >              &#9474;  
              &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                  


                  Installing symlink /usr/local/bin/et -> /usr/local/games/enemy-territory//et



ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/rl/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Software Rasterizer
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa Project
GL_RENDERER: Software Rasterizer
GL_VERSION: 2.1 Mesa 7.2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_OML_swap_method GLX_SGIS_multisample GLX_SGIX_fbconfig 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xb0725000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/rl/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/rl/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/rl/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaeb93f40  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: rl-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Software Rasterizer
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa Project
GL_RENDERER: Software Rasterizer
GL_VERSION: 2.1 Mesa 7.2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_OML_swap_method GLX_SGIS_multisample GLX_SGIX_fbconfig 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/rl/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/rl/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/rl/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae40ff40  
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

Please note that I'm a computer-novice, so you'll have to give me step-by-step instruction or else I won't know what to do.  Thank you for your help!

---

### Post by hikaricore on 2009-04-15
I can see from the error output that you're using the Mesa driver which is in no way suitable this type of application.
This is a video hardware/driver issue, please provide more info.

---

### Post by WolfETplayer on 2009-04-15
```
desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
desktop:~$ sudo lshw -C video
[sudo] password for rl: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 440 AGP 8x]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5

```

Does that help?

---

### Post by WolfETplayer on 2009-04-15
I stumbled onto this [site]("http://www.psychocats.net/ubuntu/nvidia").  The 2nd instruction:
> You'll then see that Nvidia drivers are not in use. Check (or tick) the box underneath Enabled to enable the drivers. 
Where are the Nvidia drivers?  When I click on "Hardware Drivers," it produces a blank... 

...Exactly which drivers do I have to download, and where?  You see, I'm lost.  Please help me.

I'm as slow as the game! (heh)

---

### Post by WolfETplayer on 2009-04-15
```
desktop:~$ uname -a
Linux desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

So, what kind of Nvidia driver do I need to install?

---

### Post by WolfETplayer on 2009-04-15
I'm going to download this:

[HTML]http://www.nvidia.com/object/linux_display_amd64_96.43.11.html[/HTML]

Is that OK?

---

### Post by WolfETplayer on 2009-04-15
It's not working and I really don't know what to do... Please help!

---

### Post by WolfETplayer on 2009-04-15
```
desktop:~$ sh NVIDIA-Linux-x86_64-96.43.11-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-96.43.11-pkg2.run
```

?

---

### Post by WolfETplayer on 2009-04-15
IT WORKS!!! (I used Envy and installed the recommended drivers...8))

Thanks!:)

---

### Post by WolfETplayer on 2009-04-15
Damn, there are a few other problems:  it doesn't save my profile, and every time I try to get on a server, it either doesn't load any of the maps or it exits the game... Weird.  What could the problem be?

```
Sys_LoadDll(/home/xxx/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/xxx/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/xxx/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaddeff40  
Sys_LoadDll(ui) succeeded!
Couldn't write etconfig.cfg.
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Couldn't write etconfig.cfg.
couldn't exec profiles/keller/etconfig.cfg
Script_WriteProfile: Can't write profiles/keller/profile.pid.
^3WARNING: couldn't write profiles/keller/profile.pid
execing default.cfg
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX 440 with AGP8X/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440 with AGP8X/AGP/SSE2
GL_VERSION: 1.5.8 NVIDIA 96.43.09
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_get_proc_address 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/xxx/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/xxx/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/xxx/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xadaeff40  
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
Couldn't write profiles/keller/etconfig.cfg.
Requesting servers from the master...
CL_ServersResponsePacket
112 servers parsed (total 112)
CL_ServersResponsePacket
112 servers parsed (total 224)
CL_ServersResponsePacket
112 servers parsed (total 336)
CL_ServersResponsePacket
112 servers parsed (total 448)
CL_ServersResponsePacket
112 servers parsed (total 560)
CL_ServersResponsePacket
112 servers parsed (total 672)
CL_ServersResponsePacket
112 servers parsed (total 784)
CL_ServersResponsePacket
112 servers parsed (total 896)
CL_ServersResponsePacket
112 servers parsed (total 1008)
CL_ServersResponsePacket
112 servers parsed (total 1120)
CL_ServersResponsePacket
112 servers parsed (total 1232)
CL_ServersResponsePacket
112 servers parsed (total 1344)
CL_ServersResponsePacket
112 servers parsed (total 1456)
CL_ServersResponsePacket
112 servers parsed (total 1568)
CL_ServersResponsePacket
112 servers parsed (total 1680)
CL_ServersResponsePacket
112 servers parsed (total 1792)
CL_ServersResponsePacket
112 servers parsed (total 1904)
CL_ServersResponsePacket
112 servers parsed (total 2016)
CL_ServersResponsePacket
112 servers parsed (total 2128)
CL_ServersResponsePacket
105 servers parsed (total 2233)
^3WARNING: Couldn't find image for shader levelshots/supplydepot2
^3WARNING: Couldn't find image for shader levelshots/baserace
^3WARNING: Couldn't find image for shader levelshots/supply
^3WARNING: Couldn't find image for shader levelshots/baserace_desert
^3WARNING: Couldn't find image for shader levelshots/tc_base
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
8.2.0.28:27960 resolved to 8.2.0.28:27960
^5PunkBuster Client: File /home/rl/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (1853826324)
^5PunkBuster Client: Connected to Server 8.2.0.28:27960
^5PunkBuster Client: File /home/rl/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
^5PunkBuster Client: File /home/rl/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (1853826324)
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
^5PunkBuster Client: File /home/rl/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (1853826324)
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
^5PunkBuster Client: File /home/rl/.etwolf/etmain/etkey Deleted due to Empty CDKey
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (1853826324)
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
----- FS_Startup -----
Current search path:
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
    on the pure list
/home/xxx/.etwolf/noquarter
/usr/local/games/enemy-territory/noquarter
/home/xxx/.etwolf/etmain
/usr/local/games/enemy-territory/etmain

----------------------
7526 files in pk3 files
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
couldn't exec profiles/keller/etconfig.cfg
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds2.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds2.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/rl/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
Need paks: noquarter/z_kfsounds2.pk3
noquarter/z_kfsounds.pk3
noquarter/z_caen2fix.pk3
noquarter/z_baserfin_scobo.pk3
noquarter/zz_obmapfixes.pk3
noquarter/nq_bin_b1.2.0.pk3
noquarter/noquarter_b1.2.0_fix.pk3
noquarter/noquarter_b1.2.0.pk3
noquarter/noquarter_b1.1.1.pk3
noquarter/noquarter_b1.1.0.pk3
etmain/kfnqcustoma3.pk3
etmain/kfnqcustom4.pk3
etmain/kfnqcustom2.pk3
etmain/kfnqcustom1.pk3

Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Need paks: @noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds2.pk3@noquarter/z_kfsounds.pk3@noquarter/z_kfsounds.pk3@noquarter/z_caen2fix.pk3@noquarter/z_caen2fix.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/z_baserfin_scobo.pk3@noquarter/zz_obmapfixes.pk3@noquarter/zz_obmapfixes.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/nq_bin_b1.2.0.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0_fix.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.2.0.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.1.pk3@noquarter/noquarter_b1.1.0.pk3@noquarter/noquarter_b1.1.0.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustoma3.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom4.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom2.pk3@etmain/kfnqcustom1.pk3@etmain/kfnqcustom1.pk3
Could not create noquarter/z_kfsounds2.pk3.tmp
ERROR: DL_BeginDownload unable to open '/home/xxx/.etwolf/noquarter/z_kfsounds.pk3.tmp' for writing
Failed to initialize download for 'http://pk3.gameservers.net/rtcwet/noquarter/z_kfsounds.pk3'
----- FS_Startup -----
Current search path:
/home/xxx/.etwolf/noquarter
/usr/local/games/enemy-territory/noquarter
/home/xxx/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
11289 files in pk3 files
********************
ERROR: Disconnected from server
********************
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/xxx/.etwolf/noquarter/ui.mp.i386.so
----- FS_Startup -----
Current search path:
/home/xxx/.etwolf/noquarter
/usr/local/games/enemy-territory/noquarter
/home/xxx/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
15052 files in pk3 files
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: recursive error 'Sys_LoadDll(ui) failed, no corresponding .so file found in fs_homepath or fs_basepath
' after: Disconnected from server
Shutdown tty console

```

So, what can I do to fix this?  Should I reinstall the game?  Thanks for your help!

---

### Post by R33D3M33R on 2009-04-16
You should installed the game in the home directory. Try to run it with sudo.

---

### Post by rizzeh on 2009-04-16
> **R33D3M33R said:**
> You should installed the game in the home directory. Try to run it with sudo.

I agree, for someone new to linux/ubuntu, installing games in home dir is easier (no worries about permissions). In long term though, its best to be installed somewhere in /usr. I have a separate partition at /usr/local. That way if something goes wrong OS reinstall is painless :)

---

