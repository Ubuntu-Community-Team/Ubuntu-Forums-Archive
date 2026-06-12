---
title: "Glx error for games"
date: 2004-10-18
forum: Gaming &amp; Leisure
---

### Post by ElJuifos51 on 2004-10-18
I don't know if ubuntu guys play but I ask a questionfor them..

I have installed UT 2004 and Doom 3 and in each time, I have a problem of glx 
 !!

Thanks

For UT2004 :
open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  79 (X_FreeColormap)
  Resource id in failed request:  0x240000c
  Serial number of failed request:  116
  Current serial number in output stream:  118

and for Doom3:
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Open X display
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
idRenderSystem::Shutdown()
Xlib:  extension "GLX" missing on display ":0.0".
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 34
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 39
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

---

### Post by ubuntu-geek on 2004-10-18
What kind of video card do you have? If you have a Nvidia or ATI and havent installed the cool drivers check here..

[http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by cakey on 2004-10-29
I'm having similar issues running UT2004 as well.  I DO have the nvidia drivers running.


Here's the terminal output:

_X11TransSocketOpen: socket() failed for local
_X11TransSocketOpenCOTSClient: Unable to open socket for local
_X11TransOpen: transport open failed for local/ubuntu:0
Couldn't set video mode: Could not create GL context


History:

Exiting due to error



And this is from the ut2004.log:

Log: TTS: No output filename specified.
Log: Enter SetRes: 1024x768 Fullscreen 1
Log: OpenGL
Critical: Couldn't set video mode: Could not create GL context


 :cry:

---

### Post by cakey on 2004-10-30
Oh, and I'm running a Geforce FX 5900.   :neutral:

---

### Post by cacofonix on 2004-10-30
Can you post the output of glxinfo please?

---

### Post by jdong on 2004-10-30
Try **LD_PRELOAD=/usr/lib/libGL.so.1 [game-command] **

---

### Post by cakey on 2004-10-31
[QUOTE=cacofonix]Can you post the output of glxinfo please?[/QUOTE]

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5900XT/AGP/SSE/3DNOW!
OpenGL version string: 1.5.1 NVIDIA 61.11
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite,
    GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  2 1 Ncon
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  4 1 Ncon
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  2 1 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  4 1 Ncon
0x2c 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16 16  0 0 None
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  0 0 None
0x2e 16 dc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16 16  0 0 None
0x2f 16 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16 16  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16 16  0 0 None
0x31 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  2 1 Ncon
0x32 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16 16  4 1 Ncon
0x33 16 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  2 1 Ncon
0x34 16 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16 16  4 1 Ncon


[quote=jdong]Try LD_PRELOAD=/usr/lib/libGL.so.1 [game-command][/quote]
No luck, same error.   :(

---

### Post by Moobert on 2005-01-04
[QUOTE=cakey]I'm having similar issues running UT2004 as well.  I DO have the nvidia drivers running.


Here's the terminal output:

_X11TransSocketOpen: socket() failed for local
_X11TransSocketOpenCOTSClient: Unable to open socket for local
_X11TransOpen: transport open failed for local/ubuntu:0
Couldn't set video mode: Could not create GL context


History:

Exiting due to error



And this is from the ut2004.log:

Log: TTS: No output filename specified.
Log: Enter SetRes: 1024x768 Fullscreen 1
Log: OpenGL
Critical: Couldn't set video mode: Could not create GL context


 :cry:[/QUOTE]

yeah, i got this error yesterday, after reinstalling ut2004. I fixed it my removing the folder in my home called ./ut2004, it most likely had config files relating to the other install, so removing them lets ut start again with new configs.

---

### Post by fain on 2007-08-08
I am having this problem with doom3 too 
im running 64bit fiesty and my sys specs are in my sig.

```
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ sudo doom3
Password:
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
/proc/cpuinfo CPU frequency: 3000 MHz
guessing video ram ( use +set sys_videoRam to force ) ..
Setup X display connection
found XNVCtrl extension 1.13
Detected
        3.00 GHz CPU
        2016 MB of System memory
        256 MB of Video memory on an optimal video architecture

This system qualifies for High quality!
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 800x600
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 46
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 50
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 52
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ clr
bash: clr: command not found
jay@home:~$ clear

jay@home:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

```

it acts as if its going to start but crashes with 
Sys_Error: Unable to initialize OpenGL
i tried running as root but still a no go
and pre-loading libgl doesn't work either

---

### Post by hikaricore on 2007-08-08
Thread is over two years old.  You may have better luck starting a new one.

---

