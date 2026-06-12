---
title: "How come wolfenstein enemy territory LAGS on ubuntu? HELP I BEG!"
date: 2009-04-09
forum: General Help
---

### Post by krine11 on 2009-04-09
Hi there. I jsut installed wolfenstein enemy territory right but it LAGS LIKE HELL and i dont know what is wrong with it. look ill paste what goes on when i type "et" in terminal : 

sharma@rohit-sharma:~$ et
ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/sharma/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
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
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon Xpress Series
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 2.1.8087 Release
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add  GL_EXT_compiled_vertex_array GL_S3_s3tc 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/sharma/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa8650bb4  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
ERROR: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27961
Hostname: rohit-sharma
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Couldn't write etconfig.cfg.
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
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon Xpress Series
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 2.1.8087 Release
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add  GL_EXT_compiled_vertex_array GL_S3_s3tc 
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
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/sharma/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae607bb4  
Sys_LoadDll(ui) succeeded!
Couldn't write etconfig.cfg.
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
execing preset_fast_ui.cfg
Couldn't write etconfig.cfg.
execing preset_normal_ui.cfg
Couldn't write etconfig.cfg.
execing preset_high_ui.cfg
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
Couldn't write etconfig.cfg.
couldn't exec profiles/sddsd/etconfig.cfg
execing default.cfg
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
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon Xpress Series
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 2.1.8087 Release
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add  GL_EXT_compiled_vertex_array GL_S3_s3tc 
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
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/sharma/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/sharma/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae607bb4  
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
Couldn't write profiles/sddsd/etconfig.cfg.
Requesting servers from the master...
CL_ServersResponsePacket
112 servers parsed (total 112)
CL_ServersResponsePacket
112 servers parsed (total 224)
CL_ServersResponsePacket
112 servers parsed (total 336)
CL_ServersResponsePacket
112 servers parsed (total 448)
CL_ServersResponsePacket
112 servers parsed (total 560)
CL_ServersResponsePacket
112 servers parsed (total 672)
CL_ServersResponsePacket
0 servers parsed (total 672)
^3WARNING: Couldn't find image for shader levelshots/et_mor2
^5PunkBuster Client: PunkBuster Client (v1.013 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.55 linux-i386 May 27 2003]
^5PunkBuster Client: Not Connected to a Server
Couldn't write profiles/sddsd/etconfig.cfg.
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
209.51.202.124:27994 resolved to 209.51.202.124:27994
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (527548959)
^5PunkBuster Client: Connected to Server 209.51.202.124:27994
^5PunkBuster Client: Master Query Sent to (MASTER4.EVENBALANCE.COM) 66.180.170.20
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
^5PunkBuster Client: Received Master Security Information
^5PunkBuster Client: Cdkey Registration Request sent to GuidAuth Master at 192.246.40.62:27960 (4018099110)
^5PunkBuster Client: GuidAuth Packet Ignored : File Write Error
659 servers listed in browser with 2762 players.
13 servers not listed (filtered out by game browser settings)
----- FS_Startup -----
Current search path:
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
    on the pure list
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
    on the pure list
/home/sharma/.etwolf/tcetest
/usr/local/games/enemy-territory/tcetest
/home/sharma/.etwolf/etmain
/usr/local/games/enemy-territory/etmain

----------------------
7458 files in pk3 files
Need paks: tcetest/zzz_scmappack01.pk3
tcetest/tce_x48-2-war.pk3
tcetest/tce_v48-1.pk3
tcetest/pak3.pk3
tcetest/pak2.pk3
tcetest/pak1.pk3
tcetest/pak0.pk3
tcetest/mp_bin.pk3

Need paks: @tcetest/zzz_scmappack01.pk3@tcetest/zzz_scmappack01.pk3@tcetest/tce_x48-2-war.pk3@tcetest/tce_x48-2-war.pk3@tcetest/tce_v48-1.pk3@tcetest/tce_v48-1.pk3@tcetest/pak3.pk3@tcetest/pak3.pk3@tcetest/pak2.pk3@tcetest/pak2.pk3@tcetest/pak1.pk3@tcetest/pak1.pk3@tcetest/pak0.pk3@tcetest/pak0.pk3@tcetest/mp_bin.pk3@tcetest/mp_bin.pk3
Need paks: @tcetest/zzz_scmappack01.pk3@tcetest/zzz_scmappack01.pk3@tcetest/tce_x48-2-war.pk3@tcetest/tce_x48-2-war.pk3@tcetest/tce_v48-1.pk3@tcetest/tce_v48-1.pk3@tcetest/pak3.pk3@tcetest/pak3.pk3@tcetest/pak2.pk3@tcetest/pak2.pk3@tcetest/pak1.pk3@tcetest/pak1.pk3@tcetest/pak0.pk3@tcetest/pak0.pk3@tcetest/mp_bin.pk3@tcetest/mp_bin.pk3
couldn't exec profiles/sddsd/etconfig.cfg
Client download subsystem initialized
Failed to initialize download for 'http://wolf.clan-bg.com/server//tcetest/zzz_scmappack01.pk3'
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/sharma/.etwolf/tcetest/ui.mp.i386.so
----- FS_Startup -----
Current search path:
/home/sharma/.etwolf/tcetest
/usr/local/games/enemy-territory/tcetest
/home/sharma/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
11187 files in pk3 files
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Sys_LoadDll(ui) failed, no corresponding .so file found in fs_homepath or fs_basepath






What is the big problem? Can you please tell me how to fix this lag and so i can play with my friends again. I BEG

---

### Post by pbotros1234 on 2009-04-09
Hardware specs? What kind of video card do you have? Can it run smoothly on windows for the same computer?

---

