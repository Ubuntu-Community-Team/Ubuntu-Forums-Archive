---
title: "ET Crash on startup"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by simplyw00x on 2006-07-27
Hi guys;

Hoping you can help bust a bug with me. Enemy Territory crashes as soon as the demo movie has finished, requiring a Ctrl+Alt+F1 to kill the process. This happens with sound enabled and disabled, fullscreen or windowed. I've tried clearing the server cache to no avail. Any ideas? All other GL apps are fine.

```
et +set r_fullscreen 0
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/carl/.etwolf/etmain/_play0003.pk3 (3 files)
/home/carl/.etwolf/etmain/_play0002.pk3 (4 files)
/home/carl/.etwolf/etmain/_play-1-0002.pk3 (4 files)
/home/carl/.etwolf/etmain/xvc6map.pk3 (2 files)
/home/carl/.etwolf/etmain/WhaleClient-1_2final.pk3 (24 files)
/home/carl/.etwolf/etmain/venice.pk3 (330 files)
/home/carl/.etwolf/etmain/VCamp1.pk3 (2 files)
/home/carl/.etwolf/etmain/ubuntu.pk3 (2 files)
/home/carl/.etwolf/etmain/temple3.pk3 (49 files)
/home/carl/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/carl/.etwolf/etmain/stopwatch.pk3 (2 files)
/home/carl/.etwolf/etmain/sound.pk3 (2 files)
/home/carl/.etwolf/etmain/sixmapi.pk3 (2 files)
/home/carl/.etwolf/etmain/PLC_MOD.pk3 (78 files)
/home/carl/.etwolf/etmain/panzerarena.pk3 (10 files)
/home/carl/.etwolf/etmain/pak7918.pk3 (2 files)
/home/carl/.etwolf/etmain/pak3353.pk3 (1 files)
/home/carl/.etwolf/etmain/pak3352.pk3 (1 files)
/home/carl/.etwolf/etmain/pak1427.pk3 (2 files)
/home/carl/.etwolf/etmain/normandy_final.pk3 (63 files)
/home/carl/.etwolf/etmain/marbi.pk3 (2 files)
/home/carl/.etwolf/etmain/ia.pk3 (2 files)
/home/carl/.etwolf/etmain/gentoo.pk3 (2 files)
/home/carl/.etwolf/etmain/fedora.pk3 (2 files)
/home/carl/.etwolf/etmain/ExE4.pk3 (2 files)
/home/carl/.etwolf/etmain/etmapcycle.pk3 (3 files)
/home/carl/.etwolf/etmain/eq_rtcw_et_fc.pk3 (1 files)
/home/carl/.etwolf/etmain/dna-6map.pk3 (2 files)
/home/carl/.etwolf/etmain/desertfortress.pk3 (80 files)
/home/carl/.etwolf/etmain/Desertfortress.pk3 (76 files)
/home/carl/.etwolf/etmain/debian.pk3 (2 files)
/home/carl/.etwolf/etmain/cortexbeta.pk3 (358 files)
/home/carl/.etwolf/etmain/CORE.pk3 (2 files)
/home/carl/.etwolf/etmain/btp3.pk3 (1 files)
/home/carl/.etwolf/etmain/aurox.pk3 (2 files)
/home/carl/.etwolf/etmain/6RegularMaps.pk3 (2 files)
/home/carl/.etwolf/etmain/6map.pk3 (2 files)
/home/carl/.etwolf/etmain/6cust.pk3 (2 files)
/home/carl/.etwolf/etmain/10map.pk3 (2 files)
/home/carl/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
5061 files in pk3 files
^3WARNING: profile.pid found for profile 'Carlio' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Carlio/etconfig.cfg
r_smp is unsafe. Check com_crashed.
r_mode is unsafe. Check com_crashed.
r_depthbits is unsafe. Check com_crashed.
r_stencilbits is unsafe. Check com_crashed.
r_stereo is unsafe. Check com_crashed.
r_colorbits is unsafe. Check com_crashed.
r_texturebits is unsafe. Check com_crashed.
r_clampToEdge is unsafe. Check com_crashed.
r_ext_texture_env_add is unsafe. Check com_crashed.
r_nv_fogdist_mode is unsafe. Check com_crashed.
r_ext_NV_fog_dist is unsafe. Check com_crashed.
r_ext_texture_filter_anisotropic is unsafe. Check com_crashed.
r_ati_fsaa_samples is unsafe. Check com_crashed.
r_ati_truform_pointmode is unsafe. Check com_crashed.
r_ati_truform_normalmode is unsafe. Check com_crashed.
r_ati_truform_tess is unsafe. Check com_crashed.
r_ext_ATI_pntriangles is unsafe. Check com_crashed.
r_glIgnoreWicked3D is unsafe. Check com_crashed.
r_ext_compiled_vertex_array is unsafe. Check com_crashed.
r_ext_multitexture is unsafe. Check com_crashed.
r_ext_gamma_control is unsafe. Check com_crashed.
r_ext_compressed_textures is unsafe. Check com_crashed.
r_allowExtensions is unsafe. Check com_crashed.
r_glDriver is unsafe. Check com_crashed.
execing autoexec.cfg
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
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
libGL: XF86DRIGetClientDriverName: 4.0.3 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 47, (OK)
drmOpenByBusid: drmOpenMinor returns 47
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
libGL error:
Can't open configuration file /etc/drirc: No such file or directory.
libGL error:
Warning in /home/carl/.drirc line 10, column 12: undefined option: texture_level_hack.GL_RENDERER: Mesa DRI R200 20060602 AGP 4x TCL
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI R200 20060602 AGP 4x TCL
GL_VERSION: 1.3 Mesa 6.5.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_MESA_swap_control GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_groupGL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
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
48000 speed
0x0xa7faa000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/carl/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/carl/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/carl/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa6418f40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: puzzlement
IP: 192.168.1.2
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master2.evenbalance.com
^5PunkBuster Client: Resolved to [69.59.149.240]
^5PunkBuster Client: PunkBuster Client (v1.253 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
Received signal 15, exiting...
Shutdown tty console

```

ET 2.6, Radeon 9200 Pro, DRI Radeon driver

---

### Post by blithen on 2008-01-05
Same problem here. Anyone know the answer?

---

