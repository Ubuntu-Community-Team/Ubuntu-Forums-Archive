---
title: "Enemy Territory Blank Screen"
date: 2007-01-01
forum: Gaming &amp; Leisure
---

### Post by DirtDawg on 2007-01-01
I have a Dell desktop with an intel 845G 64M graphics card(i think), 2.4 gHz Celron, 700-some-odd Ram. I installed Enemy Territory, but every time I start it, I get a blank screen. I can hear the sound and I can use "~" and "quit" to escape, but that's it. No picture. 

There's several threads about similar problems, but none seem to solve the problem. I tried the "killall esd" command to no avail. It seems like it may be a video driver problem, but I thought Intel 8xxx cards were supported more or less out-of-the box. 

Here's what I think is the relevant part of the error message:
```
  ----- finished R_Init -----
Sys_LoadDll(/home/user/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/user/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/user/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab390bb4
Sys_LoadDll(ui) succeeded!
Couldn't write etconfig.cfg.
]\quit

```

I dual boot and Enemy Territory and True Combat both work fine under Windows, so I'm sure it's not a hardware problem. Any kind of a direction would be appreciated. I'm stumped.

Thanks

---

### Post by DirtDawg on 2007-01-01
Okay so the graphics card I have is a 82845G. I found a driver from Intel [here]("http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=865&dwnldid=7485&agr=y&lang=eng&prdmap=865"). But this driver is from 2004, so it's a little old. But maybe it's better than the i810 driver I have now? (here's the relevant xorg.conf just for reference):
```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"

```

But maybe that driver is no better than the default driver and it will screw up my system? I have no eperience with video drivers. Any guidance would be great. Thanks again.

---

### Post by Zimmer on 2007-01-05
> **DirtDawg said:**
> I have a Dell desktop with an intel 845G 64M graphics card(i think), 2.4 gHz Celron, 700-some-odd Ram. I installed Enemy Territory, but every time I start it, I get a blank screen. I can hear the sound and I can use "~" and "quit" to escape, but that's it. No picture. 

There's several threads about similar problems, but none seem to solve the problem. I tried the "killall esd" command to no avail. It seems like it may be a video driver problem, but I thought Intel 8xxx cards were supported more or less out-of-the box. 

Here's what I think is the relevant part of the error message:
```
  ----- finished R_Init -----
Sys_LoadDll(/home/user/.etwolf/etmain/ui.mp.i386.so)...
S......

Sys_LoadDll(ui) succeeded!
Couldn't write etconfig.cfg.
]\quit

```

I dual boot and Enemy Territory and True Combat both work fine under Windows, so I'm sure it's not a hardware problem. Any kind of a direction would be appreciated. I'm stumped.

Thanks
before you mess with video check your permissions on etconfig.cfg and other files....
EDIT.
see
[http://ubuntuforums.org/showthread.php?t=98167](http://ubuntuforums.org/showthread.php?t=98167)  post#4 
and [http://ubuntuforums.org/showthread.php?t=80926&page=2](http://ubuntuforums.org/showthread.php?t=80926&page=2)
for details of similar problems

---

### Post by DirtDawg on 2007-01-06
Thanks Zimmer. I tried a few of the sound tweaks suggested, but it looks like it might be a fairly card or driver-specific issue. Since I'm not using an ATI chip, it seems to me like the solution linked in your post would probably not work? 

There's a [post]("http://www.forumplanet.com/PlanetWolfenstein/topic.asp?fid=6304&tid=1947371") in the ET Forums from someone also running Dapper with an Intel card and the same problems. The posts there seem to suggest the problem lie with openGl or GLX drivers that don't exist for Intel chips.

If that is the case, would the Intel driver include GLX? I tried and failed to install it (which is maybe for the best). I posted about that [here]("http://ubuntuforums.org/showthread.php?t=329359").

Here's the full output from the 'et' command, for good measure:
```

ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/dirtdawg/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
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
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
GL_VERSION: 1.3 Mesa 6.4.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

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
0x0xace35000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab2c6bb4
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: sooperbox
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
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
GL_VERSION: 1.3 Mesa 6.4.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

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
Sys_LoadDll(/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/dirtdawg/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab2c6bb4
Sys_LoadDll(ui) succeeded!
]\quit
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

---

### Post by Zimmer on 2007-01-07
[http://ubuntuforums.org/showthread.php?t=324954&highlight=i810](http://ubuntuforums.org/showthread.php?t=324954&highlight=i810)
Does not look hopeful for using your card for ET.... 
  Try glxinfo |grep direc   to see if Direct rendering is enabled,

---

### Post by DirtDawg on 2007-01-08
Thanks again Zimmer, I managed to get things running.

"glxinfo |grep direc" told me direct rendering was running. But from the thread you posted above, they mention [AIGLX]("http://en.wikipedia.org/wiki/Aiglx"), which looks like a sort of open-source XGL. Apparently Edgy has it installed by default, though not enabled, but Dapper requires installation.

There are [installation instructions for Dapper]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX") on the Beryl page. I don't think installing Beryl is necessary, but I did it for hoots. Unfortunately, using this tutorial gave me an apt-get error at first telling me it couldn't find the linux-dri-modules packages, but I found a sort of work-around [here]("http://ubuntuforums.org/showthread.php?t=317674&highlight=dapper+aiglx").

The whole endeavor made me nervous at times and took a couple hours total, but after reboting, Enemy Territory runs perfectly! Well, I haven't actually had a chance to play yet. Hopefully the performance is good, but it will have to wait until tommorow.
:mrgreen:

---

### Post by Zimmer on 2007-01-09
I shall have to investigate this AIGLX , in case I am missing something (I just sorted my ATI card as I had done for Breezy, when I upgraded ) .

Glad you can now play ET (I haven't actually re installed it myself since I moved to Dapper, no time to play recently  :(   )

---

