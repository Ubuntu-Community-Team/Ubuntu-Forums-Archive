---
title: "ET:QW White screen and grey box only!"
date: 2009-06-16
forum: Gaming &amp; Leisure
---

### Post by NateMan on 2009-06-16
I purchased two copies of ET:QW just the other day after finding it on sale for $6. After installing the game using the linux client 1.5, I attempted to run it using the program installed into my home directory. The game attempted to load, first showing a black screen and cursor, before totally whiting out the screen with a gray box. I have found a few instances of this problem but no definitive fixes seem available. I saved the output of the program from the terminal and I was given this:

```

TQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26
found interface lo - loopback
found interface wlan0 - 192.168.3.179/255.255.255.0
found interface tun0 - 130.18.90.245/255.255.255.128
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/nathan/ETQW/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /home/nathan/ETQW/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /home/nathan/ETQW/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /home/nathan/ETQW/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/nathan/ETQW/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/nathan/ETQW/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/nathan/ETQW/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/nathan/ETQW/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/nathan/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/nathan/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/nathan/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/nathan/ETQW/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /home/nathan/ETQW/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/nathan/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/nathan/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/nathan/ETQW/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /home/nathan/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/nathan/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/nathan/ETQW/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /home/nathan/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/nathan/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/nathan/ETQW/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /home/nathan/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/nathan/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/nathan/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/nathan/ETQW/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /home/nathan/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/nathan/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/nathan/ETQW/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /home/nathan/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/nathan/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/nathan/ETQW/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /home/nathan/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/nathan/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /home/nathan/ETQW/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
/home/nathan/.etqwcl/base
/home/nathan/ETQW/base
/home/nathan/ETQW/base/zpak_spanish003.pk4 (6 files)
/home/nathan/ETQW/base/zpak_spanish002.pk4 (119 files)
/home/nathan/ETQW/base/zpak_spanish001.pk4 (13 files)
/home/nathan/ETQW/base/zpak_russian003.pk4 (5 files)
/home/nathan/ETQW/base/zpak_russian002.pk4 (119 files)
/home/nathan/ETQW/base/zpak_russian001.pk4 (13 files)
/home/nathan/ETQW/base/zpak_polish003.pk4 (6 files)
/home/nathan/ETQW/base/zpak_polish002.pk4 (119 files)
/home/nathan/ETQW/base/zpak_polish001.pk4 (13 files)
/home/nathan/ETQW/base/zpak_korean003.pk4 (5 files)
/home/nathan/ETQW/base/zpak_korean002.pk4 (12 files)
/home/nathan/ETQW/base/zpak_korean001.pk4 (12 files)
/home/nathan/ETQW/base/zpak_korean000.pk4 (6 files)
/home/nathan/ETQW/base/zpak_german003.pk4 (5 files)
/home/nathan/ETQW/base/zpak_german002.pk4 (119 files)
/home/nathan/ETQW/base/zpak_german001.pk4 (13 files)
/home/nathan/ETQW/base/zpak_french003.pk4 (14 files)
/home/nathan/ETQW/base/zpak_french002.pk4 (119 files)
/home/nathan/ETQW/base/zpak_french001.pk4 (13 files)
/home/nathan/ETQW/base/zpak_english003.pk4 (7 files)
/home/nathan/ETQW/base/zpak_english002.pk4 (117 files)
/home/nathan/ETQW/base/zpak_english001.pk4 (9 files)
/home/nathan/ETQW/base/zpak_english000.pk4 (1018 files)
/home/nathan/ETQW/base/pak008.pk4 (1496 files)
/home/nathan/ETQW/base/pak007.pk4 (1510 files)
/home/nathan/ETQW/base/pak006.pk4 (3 files)
/home/nathan/ETQW/base/pak005.pk4 (2172 files)
/home/nathan/ETQW/base/pak004.pk4 (72 files)
/home/nathan/ETQW/base/pak003.pk4 (1133 files)
/home/nathan/ETQW/base/pak002.pk4 (1637 files)
/home/nathan/ETQW/base/pak001.pk4 (1067 files)
/home/nathan/ETQW/base/pak000.pk4 (9350 files)
/home/nathan/ETQW/base/game002.pk4 (3 files)
/home/nathan/ETQW/base/game001.pk4 (11 files)
/home/nathan/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
Opening IP socket: localhost:-1
thread priority set to 1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1680x1050
SDL_ListModes:
1680x1050 1600x1024 1440x900 1360x768 1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 
800x600 800x512 720x450 700x525 680x384 640x512 640x480 576x432 512x384 400x300 
320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -1076510664 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ARB_vertex_buffer_object not found
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
X..GL_ARB_multisample not found
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
X..GL_EXT_gpu_program_parameters not found
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
...using GL_EXT_texture_compression_latc
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
WARNING: vertex array range in virtual memory (SLOW)
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
486 strings read from localization/english/strings/chat.lang
884 strings read from localization/english/strings/code.lang
2187 strings read from localization/english/strings/game.lang
3208 strings read from localization/english/strings/guis.lang
3384 strings read from localization/english/strings/lifestats.lang
3522 strings read from localization/english/strings/loadtips.lang
3861 strings read from localization/english/strings/locations.lang
4386 strings read from localization/english/strings/maps.lang
4453 strings read from localization/english/strings/tasks.lang
WARNING: GL_SelectTexture: unit = 3
WARNING: GL_SelectTexture: unit = 2
WARNING: GL_SelectTexture: unit = 1
/proc/cpuinfo CPU frequency: 1596 MHz
WARNING: GL_SelectTexture: unit = 3
WARNING: GL_SelectTexture

```

Thanks in advance, I'd love to get this problem fixed so I can go on to play this game.

---

### Post by 0x3e on 2009-08-21
I had the same problem it came down to user access to /dev/nvidiactl.

check 

```
 $ glxinfo | grep direct
```
the output should be
```
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,
```

or similar and not include 

```
/dev/nvidiactl (Permission denied).
```

---

### Post by NateMan on 2009-08-21
So is the fix to change the file permissions or to own the file to my username? I imagine that changing the permissions would do it, but I'd hate to mess up my system or make it less secure by changing permissions if that is not the correct procedure. Thank you for the solution as well. That appears to be my issue.

---

