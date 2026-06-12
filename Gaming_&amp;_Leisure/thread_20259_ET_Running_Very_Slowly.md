---
title: "ET Running Very Slowly"
date: 2005-03-15
forum: Gaming &amp; Leisure
---

### Post by EvilButters on 2005-03-15
I have a Pentuim 4 with HT technology Processor, ATI 256MB Video Card, and whenver I start ET it runs so slow, the screen and the mouse...but when I close it the computer is running fine ounce again...
Processor: Intel Petuim 4 processor 2.80GHz 520 H-T Technology
Video Card: 256 MB ATI 9250 PCI
Memory: 512MB

This Is The Output I get in the terminal:

evilbutters@ubuntu:~ $ sh et
ET 2.56 linux-i386 Sep 10 2003
----- FS_Startup -----
Current search path:
/home/evilbutters/.etwolf/etmain
/home/evilbutters/enemy-territory/etmain/pak1.pk3 (10 files)
/home/evilbutters/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/evilbutters/enemy-territory/etmain/mp_bin.pk3 (4 files)
/home/evilbutters/enemy-territory/etmain

----------------------
3739 files in pk3 files
execing default.cfg
couldn't exec language.cfg
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
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
Xlib: extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect


***********************************************************
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...





That Is what I got for the first time....



evilbutters@ubuntu:~ $ sh et +set r_allowSoftwareGL 1
ET 2.56 linux-i386 Sep 10 2003
----- FS_Startup -----
Current search path:
/home/evilbutters/.etwolf/etmain
/home/evilbutters/enemy-territory/etmain/pak1.pk3 (10 files)
/home/evilbutters/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/evilbutters/enemy-territory/etmain/mp_bin.pk3 (4 files)
/home/evilbutters/enemy-territory/etmain

----------------------
3739 files in pk3 files
execing default.cfg
couldn't exec language.cfg
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
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
Xlib: extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect
...using software Mesa (r_allowSoftwareGL==1).
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_VERSION: 1.3 Mesa 4.0.4
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 6

PIXELFORMAT: color(24-bits) Z(16-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/evilbutters/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/evilbutters/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/evilbutters/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/evilbutters/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at 0x4861bbfc
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
Xlib: extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect
...using software Mesa (r_allowSoftwareGL==1).
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_VERSION: 1.3 Mesa 4.0.4
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 6

PIXELFORMAT: color(32-bits) Z(16-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/evilbutters/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/evilbutters/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/evilbutters/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/evilbutters/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at 0x4861bbfc
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

---

### Post by jensyt on 2005-03-16
As was responded to your post at [http://linux-gamers.net:](http://linux-gamers.net:)

> > You are using software Mesa (no hardware acceleration)!

Install the ATI Linux drivers. If you already have, run that crazy fgl_whatever_it_is (it's in the docs) to setup XFree / xorg.conf correctly. If you're using Mesa (concluded from your output) for some other reason and can't install the ATI drivers... it will be slow. :(
The problem, as "Fuse" indicated, is that you aren't using the hardware accelerated drivers. You need to install them before you can play anything with relatively good speed.

---

