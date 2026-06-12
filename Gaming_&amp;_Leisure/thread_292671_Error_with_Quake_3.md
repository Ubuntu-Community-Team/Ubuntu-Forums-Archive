---
title: "Error with Quake 3"
date: 2006-11-04
forum: Gaming &amp; Leisure
---

### Post by mikesena on 2006-11-04
Hi,

I've installed Quake 3 using the instructions at linux-gamers and it does work, no loss of speed or no sound, and the mouse works.

However, it randomly crashes after a short period of time.
Can someone help me figure out what's wrong?

I'm using Ubuntu Edgy 6.10.
The quake version is 1.32b
I have a 64mb imbedded graphics card, on a a50 toshiba laptop.  when i had windows, quake 3 worked perfectly with no problems.

Running glxinfo i get:
```

meo@meo-laptop:~$ glxinfo | grep "direct"
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
meo@meo-laptop:~$ 

```

Here's my crash report.


```

meo@meo-laptop:~$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/meo/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
libGL warning: 3D driver claims to not support visual 0x4b
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
GL_VERSION: 1.3 Mesa 6.5.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
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
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
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
0xaeef0000 dma buffer
No background file.
----------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost
Alias: meo-laptop
Alias: meo-laptop
IP: 127.0.0.1
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
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
31 servers parsed (total 1263)
CL_ServersResponsePacket
112 servers parsed (total 1375)
CL_ServersResponsePacket
112 servers parsed (total 1487)
CL_ServersResponsePacket
112 servers parsed (total 1599)
trying levelshots/Q3W2.TGA...
Resolving update.quake3arena.com
update.quake3arena.com resolved to 192.246.40.56:27951
220.245.163.133:27960 resolved to 220.245.163.133:27960
Resolving authorize.quake3arena.com
authorize.quake3arena.com resolved to 192.246.40.56:27952
----- FS_Startup -----
Current search path:
/home/meo/.q3a/InstaUnlagged
/usr/local/games/quake3/InstaUnlagged
./quake3.x86/InstaUnlagged
/home/meo/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
8146 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
GL_VERSION: 1.3 Mesa 6.5.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
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
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
----- finished R_Init -----
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
Loading vm file vm/cgame.qvm.
VM file cgame compiled to 786818 bytes of code
cgame loaded in 5380768 bytes on the hunk
stitched 2 LoD cracks
...loaded 6518 faces, 312 meshes, 99 trisurfs, 33 flares
CL_InitCGame:  5.91 seconds
67 msec to draw all images
Com_TouchMemory: 0 msec
execing q3config.cfg
[mEo!]^7 entered the game

WELCOME TO AN INSTA-UNLAGGED SERVER!           Neil Toronto and Aaron Storck, 
Version 1.1
-----------------------------------------------------------------------------
This server will make up for lag when you fire an instant-hit weapon, such as the railgun.  DO NOT lead your shots with these types of weapons.  Aim as you would in a single-player game.

This server will make up for your ping when you fire a projectile-firing weapon, such as the rocket launcher. This does not mean that you should not lead your shots when using projectile weapons, it simple means that you should not over-lead your shots in attempt to compensate for your lag when firing these weapons.

It cannot recover lost packets or reduce your ping.

Checkout http:\\[www.digitaldelay.net\InstaUnlagged\](www.digitaldelay.net\InstaUnlagged\), for more Info.



young un^7 was railed by drunken_monkie^7
young un^7: ^2ctf is very alive
young un^7: ^2but only euro
]name "[mEo!]"
[mEo!]^7: ^2name [mEo!]
]/name "[mEo!]"
^1S^3coob^1y^7: ^2cant play it only have p3 system
[mEo!]^7 was railed by ^4Lou^1Shiffe^7
drunken_monkie^7 was railed by ^4Lou^1Shiffe^7
young un^7: ^2ahh
young un^7: ^2:90
young un^7: ^2:(*
quake3.x86: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Received signal 6, exiting...
Shutdown tty console

```

---

### Post by mikesena on 2006-11-05
anyone?

---

