---
title: "Doom3 not working - Lucid lynx"
date: 2010-05-19
forum: Gaming &amp; Leisure
---

### Post by Dezemerel on 2010-05-19
Hi to Everyone. :)

Im having some troubles while trying to run the doom3 client in Lucid.

I had previously managed to get the client ruining in karmic flawlessly, however, I updated my system to lucid (fresh install), and the game wont run at all.

My system specs:
- ATI 5750 (With ati catalyst drivers 10.4 x64)
- Sound through alsa or oss (makes no difference).

Below is the full output resulting from running the client.

alvaro@Devorador:~/Escritorio$ /home/alvaro/Escritorio/doom3 
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: Devorador
local IP: 127.0.1.1
------ Initializing File System ------
Loaded pk4 /home/alvaro/Programas/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /home/alvaro/Programas/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /home/alvaro/Programas/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/alvaro/Programas/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/alvaro/Programas/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/alvaro/Programas/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/alvaro/Programas/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/alvaro/Programas/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/alvaro/Programas/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/alvaro/Programas/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/alvaro/Programas/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/alvaro/Programas/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/alvaro/Programas/doom3/base/pak008.pk4 with checksum 0x23ae5993
Loaded pk4 /home/alvaro/Programas/doom3/base/zpak000.pk4 with checksum 0xfaa41155
Current search path:
/home/alvaro/.doom3/base
/home/alvaro/Programas/doom3/base
/home/alvaro/Programas/doom3/base/zpak000.pk4 (830 files)
/home/alvaro/Programas/doom3/base/pak008.pk4 (3 files)
/home/alvaro/Programas/doom3/base/pak007.pk4 (38 files)
/home/alvaro/Programas/doom3/base/pak006.pk4 (48 files)
/home/alvaro/Programas/doom3/base/pak005.pk4 (63 files)
/home/alvaro/Programas/doom3/base/pak004.pk4 (5137 files)
/home/alvaro/Programas/doom3/base/pak003.pk4 (4676 files)
/home/alvaro/Programas/doom3/base/pak002.pk4 (6120 files)
/home/alvaro/Programas/doom3/base/pak001.pk4 (8972 files)
/home/alvaro/Programas/doom3/base/pak000.pk4 (2698 files)
/home/alvaro/Programas/doom3/base/game03.pk4 (2 files)
/home/alvaro/Programas/doom3/base/game02.pk4 (2 files)
/home/alvaro/Programas/doom3/base/game01.pk4 (2 files)
/home/alvaro/Programas/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
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
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: ATI Radeon HD 5700 Series 
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.22
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
Cg not available.
---------------------------------
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 74
GLXBadRenderRequest

glprogs/test.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 79
GLXBadRenderRequest

glprogs/interaction.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 84
GLXBadRenderRequest

glprogs/interaction.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 89
GLXBadRenderRequest

glprogs/bumpyEnvironment.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 94
GLXBadRenderRequest

glprogs/bumpyEnvironment.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 99
GLXBadRenderRequest

glprogs/ambientLight.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 104
GLXBadRenderRequest

glprogs/ambientLight.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 109
GLXBadRenderRequest

glprogs/shadow.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 114
GLXBadRenderRequest

glprogs/R200_interaction.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 119
GLXBadRenderRequest

glprogs/nv20_bumpAndLight.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 124
GLXBadRenderRequest

glprogs/nv20_diffuseColor.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 129
GLXBadRenderRequest

glprogs/nv20_specularColor.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 134
GLXBadRenderRequest

glprogs/nv20_diffuseAndSpecularColor.vpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 139
GLXBadRenderRequest

glprogs/environment.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 144
GLXBadRenderRequest

glprogs/environment.vfpFatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 1
  Serial number of failed request: 149
GLXBadRenderRequest

-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

Thank you for taking the time to read this post.

---

### Post by juancarlospaco on 2010-05-19
*Try Installer version 1.1 and dont update the installer...*

---

### Post by hikaricore on 2010-05-19
Is your card suppored by the latest driver and the new version of X?
I know ati dropped some support for older cards last year but I'm not familiar with which ones.

---

### Post by ELD on 2010-05-19
> **hikaricore said:**
> Is your card suppored by the latest driver and the new version of X?
I know ati dropped some support for older cards last year but I'm not familiar with which ones.

ATI 5750 is one of the latest cards to come out. "5" series are the newest ;)

---

### Post by hikaricore on 2010-05-19
Figured it was worth mentioning just incase.

---

### Post by joeelmex on 2010-05-19
I read that the new series of cards are not properly supported in Linux with the default driver that Ubuntu loads. I will remove the ubuntu drivers and try the closed source ones from Ati. If I recall correctly they just release the new catalyst driver like 2 weeks ago. I been wanting to build a new pc but the New Nvidia cards are way to power hungry and the Ati cards are a better value. Unfortunately no real gaming support for them. :(

---

### Post by Dezemerel on 2010-05-20
Hi to everyone!

First of all, thank you for your replies.

I have used the intaller v1.1.x of the doom 3 client (dont remer exactly the last numbers).
Also, as others have pointed, im using the latest ATI propietary drivers, and the card is suported in Linux.

The thing is, that I did play with this same setup in Karmic, and had no problems.  ](*,)


More suggestions would greatly be appreciated.

---

### Post by Dezemerel on 2010-05-20
Hi again!

I have been able to solve the error I previously reported in this post; It seems that I forgot to reinstall the ATI proprietary drivers after a Kernel update. (My fault, Im sorry).

However, I still haven't been able to run the game; It seems that a library required by the game is broken. This is the error displayed when I try to run the game now:

-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /home/alvaro/Programas/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/alvaro/.doom3/base/gamex86.so
**dlopen '/home/alvaro/.doom3/base/gamex86.so' failed: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)**
Regenerated world, staticAllocCount = 0.
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

Im running in a x64 system. libstdc is installed, as is GCC (but v4.4, since version 4.2 doesnt appear in the repositories).

Does some of you have any ideas of how to solve this problem?

Many thanks

---

### Post by formaldehyde_spoon on 2010-05-20
> **Dezemerel said:**
> Hi again!

I have been able to solve the error I previously reported in this post; It seems that I forgot to reinstall the ATI proprietary drivers after a Kernel update. (My fault, Im sorry).

However, I still haven't been able to run the game; It seems that a library required by the game is broken. This is the error displayed when I try to run the game now:

-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /home/alvaro/Programas/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/alvaro/.doom3/base/gamex86.so
**dlopen '/home/alvaro/.doom3/base/gamex86.so' failed: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)**
Regenerated world, staticAllocCount = 0.
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

Im running in a x64 system. libstdc is installed, as is GCC (but v4.4, since version 4.2 doesnt appear in the repositories).

Does some of you have any ideas of how to solve this problem?

Many thanks

I haven't seen the ''...version X...'' stuff before, but usually if a program wants an older version of a library that you have installed you can fix it by going to /usr/lib and entering: 
ln -s yourCurrentLibraryFile.so libgcc_s.so.1

---

