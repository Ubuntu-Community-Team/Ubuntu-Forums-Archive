---
title: "Enemy Territory and derivities = No Sound"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2006-10-28
I just installed Enemy territory with out a hitch except for when i start the gave i have no sound!! Here is the game output:```
Log of et 
Sat Oct 28 16:21:34 2006

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/collin/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Collin/etconfig.cfg
couldn't exec autoexec.cfg
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
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: RADEON XPRESS Series Generic
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: RADEON XPRESS Series Generic
GL_VERSION: 2.0.6065 (8.29.6)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ARB_draw_buffers GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_get_proc_address GLX_ARB_multisample 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/collin/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/collin/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/collin/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa57edf40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: RekahSoft
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v1.152 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

Sat Oct 28 16:21:49 2006
----------------
```I also included the log as a file (et.log). How do i  get sound in Enemy Territory and derivatives.

---

### Post by Monkus on 2006-10-28
I too am having the same problem with sound on ET. And as fate would have it. I spell Collin with 2 "L"s also. Perhaps it's a problem that only occurs if you spell it with 2 "L"'s"

---

### Post by halfvolle melk on 2006-10-28
Copy/paste from [http://katanoon.nl/ubu-e/install.php](http://katanoon.nl/ubu-e/install.php)

> Step 4: Fixing sound issues
 If your sound didn't work in Step 3, then try the following: 
 sudo -s
 echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
 echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
 exit
 

Exit all music players, web browsers etc. then try: 
 killall esd
 et 

If you now have sound, then: 
 sudo -s
 echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
 echo "echo "et.x86 0 0 disiable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
 exit 
 This will save the setting.

---

### Post by rekahsoft on 2006-10-28
> **halfvolle melk said:**
> Copy/paste from [http://katanoon.nl/ubu-e/install.php](http://katanoon.nl/ubu-e/install.php)

nope...didn't work :'(

---

### Post by rekahsoft on 2006-10-30
anybody?

---

### Post by mattias01 on 2006-11-01
> sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

> **rekahsoft said:**
> anybody?
It worked for me. Thanks!

---

### Post by humble.life on 2007-12-13
This solution does not work for me, where is the support??

---

### Post by happysmileman on 2007-12-13
> et-sdl-sound (Run ET With ALSA) 

There is an alpha hack which is around that makes Return To Castle Wolfenstein Enemy Territory play with ALSA by replacing standard sound system functions in runtime as aoss won't work for ET. I found this necessary when wanting to run TeamSpeak 2.XX at the same time. 

It's located at [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/) 

Simply download the latest tarball [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.tar.gz) 

1. Extract 

2. Copy et-sdl-sound.so file to /opt/enemy-territory/ 

3. Open your favourite text editor and add the following lines and save as et_sdl_sound.sh: 
#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /opt/enemy-territory/
LD_PRELOAD="/opt/enemy-territory/et-sdl-sound.so" ./et.x86 $*

4. chmod +x et_sdl_sound.sh 

5. ./et_sdl_sound.sh 

Note if you want to hook this up to XQF you need to tell XQF that the "Command Line" is "/opt/enemy-territory/et_sdl_sound.sh" and the "Working Directory" is "/opt/enemy-territory/"

That works for me in Gentoo, I'm pretty sure it also worked in Ubuntu as well, worth a shot

---

### Post by findus on 2008-12-21
> **halfvolle melk said:**
> Copy/paste from [http://katanoon.nl/ubu-e/install.php](http://katanoon.nl/ubu-e/install.php)

Worked for me too!

Cheers!

---

