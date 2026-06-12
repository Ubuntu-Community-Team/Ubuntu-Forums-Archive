---
title: "doom 3 wont start"
date: 2006-09-07
forum: Gaming &amp; Leisure
---

### Post by nbpetts on 2006-09-07
I am having some reall problems with my Doom 3 install.  I have run the install script, and copied the .pak files.  when i run the command doom3, it initilizez for a bit then exits the program (error messages will be included)  Any ideas?


system specs.
Athalon 2200
gForce 6600 
512g DDR3200
Ubuntu Dapper 6.06

```
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 71.201.21.223/255.255.254.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/nbpetts/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
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
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 6600/PCI/SSE2/3DNOW!
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_fragment_program GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.10
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 15052 frames ( 60208 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
X..GL_ARB_texture_compression not found
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
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
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

```

---

### Post by Dark Elitist on 2006-09-07
What videocard chipset do you have? nVidia, ATI, or other? Also, how much ram do you have? Did you install the drivers for your videocard?

Always provide system specifications in any post such as this or posters will be of little help.

---

### Post by nbpetts on 2006-09-08
> **Dark Elitist said:**
> What videocard chipset do you have? nVidia, ATI, or other? Also, how much ram do you have? Did you install the drivers for your videocard?

Always provide system specifications in any post such as this or posters will be of little help.

system specs now in op.  So, i did some deep searching, and i have found that the problem is caused by the fact that i installed xgl and that disables direct rendering.  i have disabled xgl, and reinstalled my drivers (nvidia).  However, when i do glxinfo | grep rendering it still tells me that direct rendering is not operating.  How can i enable direct rendering?

thanks

---

### Post by danembraceddc on 2006-09-08
One thing that may help is to search the forum for nonXgl. I havent gotten doom3 to run yet with nonXgl but some other opengl gmaes have worked.

---

### Post by nbpetts on 2006-09-11
ok, i got it fixed.   This error does indeed have to do with the direct rendering not being enabled. For reasons byond me, i had to reinstall my nvidia drivers twice before the install took.  dont know. thanks for all the help

nbpetts

---

