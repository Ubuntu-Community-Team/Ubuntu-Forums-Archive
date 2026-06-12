---
title: "doom3 wont run need help"
date: 2006-12-23
forum: Gaming &amp; Leisure
---

### Post by feardotcom on 2006-12-23
i installed doom3, transfered all the pk4's, and cfg file to the base directory in /usr/local/games/doom3, and then i goto command line and type doom3 and this is the error it gives me.

DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.15.100/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Current search path:
/home/chris/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
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
4966 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
4966 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
Fatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 2
  Serial number of failed request: 60
XF86DGANoDirectVideoMode

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 6, frequency: 44100
allocated a mix buffer of 49152 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_EXT_stencil_wrap not found
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
using ARB renderSystem
Regenerated world, staticAllocCount = 0.
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 137
  Minor opcode of failed request: 2
  Serial number of failed request: 481
XF86DGANoDirectVideoMode
Sys_Error: couldn't find game dynamic library





can someone please help me.](*,)

---

### Post by ceno-byte on 2006-12-23
it may be because it is installed in the root directory rather then your home folder try using
"sudo ./doom3" to see if that works

PS: you might wanna post your specs as well just to be safe that it is not a hardware problem

---

### Post by zedd2006 on 2006-12-23
sorry i had to start a new account, log in problems with feardotcom, i dontknow why, but anyway, i have a P4 HT 3ghz, 1.5gb of ram, radeon x300 128mb video card, i tried the sudo ./doom3 it didn;t work, so i tried sudo doom3 and it did the same thing as just launching doom3, it pops up acts like its gonna load and 4 seconds later it closes the game.](*,)

---

### Post by -deadcats on 2006-12-23
If you've installed the binaries, "doom3-linux-1.3.1302.x86.run" and copied the .pak files correctly over to "/usr/ocal/games/doom3" overwriting the entire directory, then it should easily run from a terminal with the simple command, "doom3".

However, if you're trying to run it from the Debian games entry screen, that typically has only the game server command, in which case you should change ".../doom3 -dedicated" to ".../doom3"

And that will start the single player game. How to do anything else? Sorry, not me.

best wishes,
-dc

---

### Post by zedd2006 on 2006-12-24
the "doom3 -dedicated" did the same thing as just "doom3" or click on my shortcut tot he game.

---

