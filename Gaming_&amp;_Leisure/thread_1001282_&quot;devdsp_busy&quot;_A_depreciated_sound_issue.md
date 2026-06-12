---
title: "&quot;/dev/dsp/ busy&quot; A depreciated sound issue"
date: 2008-12-03
forum: Gaming &amp; Leisure
---

### Post by ubuntoooooo on 2008-12-03
My problem is there is no sound in the particular version of Return to Castle Wolfenstein v1.1. I choose to play this version because of, well, no reason. I just like the drop gun antics, the community... yeah.

I found a script written (et-sdl-sound) for 1.41 RTCW and one for 2.60b RTCW:ET (Tested and works)

```
Wolf 1.1-MP linux-i386 Dec 25 2001
----- FS_Startup -----
Current search path:
/home/will/.wolf/main
/usr/local/games/wolfenstein/main/mp_S4NDMoD_Font_02.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_S4NDMoD_Font_01.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_pakmaps0.pk3 (21 files)
/usr/local/games/wolfenstein/main/mp_pak2.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_pak1.pk3 (308 files)
/usr/local/games/wolfenstein/main/mp_pak0.pk3 (783 files)
/usr/local/games/wolfenstein/main/S4NDMoD_Hitsounds_00.pk3 (7 files)
/usr/local/games/wolfenstein/main/pak0.pk3 (4775 files)
/usr/local/games/wolfenstein/main
./wolf.x86/main

----------------------
5903 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig_mp.cfg
usage: seta <variable> <value>
com_zoneMegs will be changed upon restarting.
execing autoexec.cfg
usage: seta <variable> <value>
Hunk_Clear: reset the hunk ok
Joystick is not active.
logfile opened on Wed Dec  3 18:25:37 2008

Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Loaded 714 translation strings from scripts/translation.cfg
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8600 GTS/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GTS/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 177.82
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(16-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: enabled
HACK: using vertex lightmap approximation
Forcing glFinish
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
[COLOR="Red"]/dev/dsp: Device or resource busy
Could not open /dev/dsp[/COLOR]
------------------------------------
Sound memory manager started
Sys_LoadDll(/usr/local/games/wolfenstein/main/ui.mp.i386.so)... 
Sys_LoadDll(ui) found **vmMain** at  0xa38f7970  
Sys_LoadDll(ui) succeeded!
trying ui/assets/button_back.TGA...
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: will-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
]/quit
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
```

Otherwise the game and everything about it runs great. I've searched a lot, but I don't know yet what I'm trying to find.

---

### Post by maddog46113 on 2008-12-04
> **ubuntoooooo said:**
> My problem is there is no sound in the particular version of Return to Castle Wolfenstein v1.1. I choose to play this version because of, well, no reason. I just like the drop gun antics, the community... yeah.

I found a script written (et-sdl-sound) for 1.41 RTCW and one for 2.60b RTCW:ET (Tested and works)

```
Wolf 1.1-MP linux-i386 Dec 25 2001
----- FS_Startup -----
Current search path:
/home/will/.wolf/main
/usr/local/games/wolfenstein/main/mp_S4NDMoD_Font_02.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_S4NDMoD_Font_01.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_pakmaps0.pk3 (21 files)
/usr/local/games/wolfenstein/main/mp_pak2.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_pak1.pk3 (308 files)
/usr/local/games/wolfenstein/main/mp_pak0.pk3 (783 files)
/usr/local/games/wolfenstein/main/S4NDMoD_Hitsounds_00.pk3 (7 files)
/usr/local/games/wolfenstein/main/pak0.pk3 (4775 files)
/usr/local/games/wolfenstein/main
./wolf.x86/main

----------------------
5903 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig_mp.cfg
usage: seta <variable> <value>
com_zoneMegs will be changed upon restarting.
execing autoexec.cfg
usage: seta <variable> <value>
Hunk_Clear: reset the hunk ok
Joystick is not active.
logfile opened on Wed Dec  3 18:25:37 2008

Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Loaded 714 translation strings from scripts/translation.cfg
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8600 GTS/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GTS/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 177.82
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(16-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: enabled
HACK: using vertex lightmap approximation
Forcing glFinish
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
[COLOR="Red"]/dev/dsp: Device or resource busy
Could not open /dev/dsp[/COLOR]
------------------------------------
Sound memory manager started
Sys_LoadDll(/usr/local/games/wolfenstein/main/ui.mp.i386.so)... 
Sys_LoadDll(ui) found **vmMain** at  0xa38f7970  
Sys_LoadDll(ui) succeeded!
trying ui/assets/button_back.TGA...
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: will-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
]/quit
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
```

Otherwise the game and everything about it runs great. I've searched a lot, but I don't know yet what I'm trying to find.

Are you running Gnome or KDE, Ive heard of this bug with Wolfstein in KDE.

Are you using Alsa or OSS?

---

### Post by ubuntoooooo on 2008-12-04
Running Gnome, as for the sound thing I'm not sure how I would go about finding this out. Although I'm guessing it's Alsa.

---

### Post by maddog46113 on 2008-12-04
> **ubuntoooooo said:**
> Running Gnome, as for the sound thing I'm not sure how I would go about finding this out. Although I'm guessing it's Alsa.

Click your volume control there is a drop down box that tells you what mixer you are using. 

You might try oss when playing the game,or vice versa.

---

### Post by ubuntoooooo on 2008-12-04
Yeah I just ran through the lot of them, pulse, alsa, oss. No sound in the program, but sound throughout the desktop still.

---

### Post by maddog46113 on 2008-12-04
> **ubuntoooooo said:**
> Yeah I just ran through the lot of them, pulse, alsa, oss. No sound in the program, but sound throughout the desktop still.

Im no expert im still learning if it was a winblows issue i would have had a solution yesterday. However it sounds to me like your sound device can only process so many sounds... You might try closing anything that could be using the device before launching the game. If that dont work im all out of suggestions :( I'll do some googling and see if cant find a fix.

---

### Post by ubuntoooooo on 2008-12-04
All help is more than appreciated, I'm also a windows user primarily - Just trying to make the switch over.

---

### Post by ubuntoooooo on 2008-12-19
(bump)
I've kinda left the problem, but as I've come back to it this evening I'm still at a loss as to what to do.
Any ideas?

edit: I've seen some people used to have problems with the game running using OSS sound. How would I switch it to use a different one?

edit2: something new as I've been exploring the issue, I have a new read instead of "busy" it says:

```
------- sound initialization -------
Cmd_AddCommand: play already defined
Cmd_AddCommand: music already defined
Cmd_AddCommand: streamingsound already defined
Cmd_AddCommand: s_list already defined
Cmd_AddCommand: s_info already defined
Cmd_AddCommand: s_stop already defined
/dev/dsp: Bad file descriptor
Sound driver too old
------------------------------------

```

---

