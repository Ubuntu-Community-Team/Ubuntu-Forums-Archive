---
title: "Return to Castle Wolfenstein"
date: 2005-10-22
forum: Gaming &amp; Leisure
---

### Post by rsulli55 on 2005-10-22
I downloaded the Return to Castle Wolfenstein single player demo and installed it fine, but it won't run. This is what I get.
ryan@ubuntu:~$ wolfspdemo
Wolf 1.1b linux-i386 Jan 17 2002
----- FS_Startup -----
Current search path:
/home/ryan/.wolf-spdemo/main
/usr/local/games/wolfenstein-spdemo/main
./wolfsp.x86/main

----------------------
0 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ryan/.wolf-spdemo/demomain
/usr/local/games/wolfenstein-spdemo/demomain/pak0.pk3 (2474 files)
/usr/local/games/wolfenstein-spdemo/demomain
./wolfsp.x86/demomain

----------------------
2474 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec wolfconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf or current dir: /usr/local/games/wolfenstein-spdemo/libGL.so: cannot open shared object file: No such file or directory
failed
...loading libMesaVoodooGL.so.3.1: QGL_Init: Can't load libMesaVoodooGL.so.3.1 from /etc/ld.so.conf or current dir: /usr/local/games/wolfenstein-spdemo/libMesaVoodooGL.so.3.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by seethru on 2005-10-22
32 or 64bit system? what happens when you run glxinfo? what about glxgears?

---

### Post by rsulli55 on 2005-10-23
32, when I run glxgears a program pops out showing working gears, and when I do glx info I get.
```
ryan@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 MX/AGP/SSE2
OpenGL version string: 1.5.3 NVIDIA 76.67
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
```

---

### Post by seethru on 2005-10-23
odd, because it looks like RTCW is trying to load mesa...

...loading libMesaVoodooGL.so.3.1: QGL_Init: Can't load libMesaVoodooGL.so.3.1 from /etc/ld.so.conf or current dir: /usr/local/games/wolfenstein-spdemo/libMesaVoodooGL.so.3.1: cannot open shared object file: No such file or directory
failed.

Out of curiosity, do you have libgl1-mesa installed? I'm not sure why it's trying to load it, but make sure you have that installed.

---

### Post by rsulli55 on 2005-10-23
Sorry, but how would I install that?
EDIT: Nevermind.  This is what I get.
ryan@ubuntu:~$ sudo apt-get install libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by rsulli55 on 2005-10-23
Anyone?

---

### Post by SavageBeginner on 2005-10-30
Wolf can't find libGL.so.  For some reason it's named "libGL.so.1.2" in Ubuntu.
Just create a link to it with the name Wolf wants.

In terminal: 
sudo ln /usr/lib/libGL.so.1.2 /usr/lib/libGL.so

---

### Post by forrestcupp on 2006-08-21
install the libGL dev files

---

### Post by fakie_flip on 2006-11-06
I'm trying the same thing when I get home again. Did it work? I think you are missing some packages pkg files from the original cd even though it says it's a demo.

---

### Post by ehwelbon on 2010-08-29
This thread is old but I did want to add this.  When installing the game using the procedure in [https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein](https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein) you may run into an issue where the startup fails while listing the GL_EXTENSIONS for the driver.

The problem is that the format string buffer that prints the GL_EXTENSIONS is too small to contain the enormous number of extensions in later drivers.   What I did was to edit (yes edit, with vim) the startup program /usr/local/games/wolfenstein/wolfsp.x86

I changed the string "GL_EXTENSIONS: %s" to be this "GL_EXTENSIONS:  s".  Note that quotations are not part of the string.   The percent symbol simply becomes a space.  No other change should be made, just change this one character.

Before you change the file, make a backup copy.

I don't post very often but I am not a Linux/Ubuntu newbie.

---

