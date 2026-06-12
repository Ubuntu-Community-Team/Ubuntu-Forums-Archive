---
title: "Quake3 with Voodo3 card doesn't work"
date: 2005-11-08
forum: Gaming &amp; Leisure
---

### Post by Robo-X on 2005-11-08
I tried running Quake3 on my old PC with a Voodoo3 card and it tries to switch resolutions then exits with this message.

HACK: approxmimating cinematic for Rage Pro or Voodoo
Received signal 11, exiting...

How do I make the game run with the Voodoo 3 card? Do I have to install anything to make it work? I installed the libglide3 like it said in the [ubuntu wiki](https://wiki.ubuntu.com/Voodoo3doesnotdo3d?highlight=%28voodoo3%29). Still no go. :(

//Rob

Here is the complete quake3 log:

```

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/rob/.q3a/baseq3
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
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
libGL warning: 3D driver claims to not support visual 0x35
libGL warning: 3D driver claims to not support visual 0x36
libGL warning: 3D driver claims to not support visual 0x39
libGL warning: 3D driver claims to not support visual 0x3a
libGL warning: 3D driver claims to not support visual 0x3d
libGL warning: 3D driver claims to not support visual 0x3e
libGL warning: 3D driver claims to not support visual 0x41
libGL warning: 3D driver claims to not support visual 0x42
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa DRI 20040719 Voodoo3
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: VA Linux Systems, Inc.
GL_RENDERER: Mesa DRI 20040719 Voodoo3
GL_VERSION: 1.2 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_env_add GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_func_separate GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_HP_occlusion_test GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_window_pos GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 256
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(16-bits) Z(16-bit) stencil(0-bits)
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
0xaef70000 dma buffer
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
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v0.993 | A0) **DISABLED**
^3PunkBuster Server: PunkBuster Server (v0.993 | A0 C0.0) **DISABLED**
HACK: approxmimating cinematic for Rage Pro or Voodoo
Received signal 11, exiting...
Shutdown tty console

```

---

