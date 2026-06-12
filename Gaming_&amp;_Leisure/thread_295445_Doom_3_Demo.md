---
title: "Doom 3 Demo"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by ZERO_SHIFT on 2006-11-08
I just installed Dooom 3 Demo on my Desktop:

> 3.0 Ghz Intel P4
1GB RAM
256 nVIDIA Graphic Card
Ubuntu 6.06

The installation went fine but when I ran the demo I got this:
```
zaid@Johnny:~$ doom3-demo
DOOM 1.1.1282 linux-x86 Oct  4 2004 08:27:55
Hostname: Johnny
IP: 127.0.1.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3-demo/demo/demo00.pk4 with checksum 0x93fac1e4
Current search path:
/home/zaid/.doom3-demo/demo
/usr/local/games/doom3-demo/demo
/usr/local/games/doom3-demo/demo/demo00.pk4 (12234 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Open X display
Initializing OpenGL display
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 6600 LE/PCI/SSE2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
----------- OSS Sound Initialization -----------
opened sound device '/dev/dsp'
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
WARNING: mmap 32768 bytes on device /dev/dsp failed: Input/output error

close sound device
WARNING: sound subsystem disabled

------------------------------------------------
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
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
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
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
idRenderSystem::Shutdown()

```

What should I do?

Thanks in Advance

---

### Post by Brynster on 2006-11-08
I could be way off the mark but it looks like your video card driver is not compatable. If you are running either a Nvidia based card or ATi based card installing the drivers may assist. Either through a installer Like Automatixs, EasyUbuntu etc or though the driver packages in Synaptec or from yhr different manufacturers websites. (sorry not very techie so i cannot explain how).

---

### Post by ZERO_SHIFT on 2006-11-08
I already have my nVidia driver installed. I have Enemy Territory working as well as xgl. So I doubt that its the graphic card problem.

---

### Post by Jonne on 2006-11-17
I have the same problem.
I'm running Ubuntu Edgy, I have an nvidia card (and driver was installed fine), I have XGL and Beryl running fine, but for some reason the doom III demo gives the same 'vertex array' error. Did the OP manage to fix his problem, or does anyone else know anything that could help?

---

### Post by ZERO_SHIFT on 2006-11-18
Anyone with any ideas? Please give us your feedback.

Thanks in advance.

---

### Post by Shatrat on 2006-11-18
Both of you mentioned that you had XGL working, I've had better success with games, higher FPS and fewer problems, when I dont have any desktop eye candy stuff running like xgl, aiglx, beryl, compiz, that sort of stuff.

"WARNING: vertex array range in virtual memory (SLOW)"
Maybe a hint that you have too much stuff going on at once?

---

### Post by ZERO_SHIFT on 2006-11-21
The problem is in the installation phase, not with the launching of the demo. So I don't thing the eye candy has anything to do with it.

I did play Wolfenstien on linux with XGL running.

Any help here is much appreciated.

---

### Post by Jonne on 2006-11-21
I'm plannning on removing all XGL stuff, and trying it again. It's probably not installed properly anyway.

But it won't be for today...

---

