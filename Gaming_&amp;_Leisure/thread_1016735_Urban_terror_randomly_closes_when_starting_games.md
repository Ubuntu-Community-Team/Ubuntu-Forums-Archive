---
title: "Urban terror randomly closes when starting games"
date: 2008-12-20
forum: Gaming &amp; Leisure
---

### Post by civillian on 2008-12-20
I just installed urban terror from the getdeb website's debfiles and it startes fine (gets to the setup and main menus) but when I want to start a server or join a server when it's loading the game crashes, with the following output

```
ioQ3 1.35urt linux-i386 Aug 10 2008
----- FS_Startup -----
Going through search path...

----------------------
8032 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8400 GS/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8400 GS/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 180.16
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x9710880 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 233 milli seconds
UI menu load time = 152 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: john-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
29 arenas parsed
------ Server Initialization ------
Server: ut4_abbey
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Going through search path...

----------------------
16064 files in pk3 files
Loading vm file vm/qagame.qvm...
VM file qagame compiled to 1870844 bytes of code
qagame loaded in 34524832 bytes on the hunk
------- Game Initialization -------
gamename: q3ut4
gamedate: Dec 21 2007
2 teams with 31 entities
-----------------------------------
-----------------------------------
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8400 GS/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 180.16
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 238 milli seconds
UI menu load time = 160 milli seconds
16 bots parsed
13 crosshairs parsed
Loading vm file vm/cgame.qvm...
VM file cgame compiled to 1617707 bytes of code
cgame loaded in 34383680 bytes on the hunk
^3WARNING: invalid cull parm 'front' in shader 'textures/tub/sn_rail1t'
^3WARNING: invalid cull parm 'front' in shader 'textures/tub/sn_rail1t'
^3WARNING: invalid cull parm 'front' in shader 'textures/tub/sn_rail1t'
^3WARNING: invalid cull parm 'front' in shader 'textures/tub/sn_rail1t'
^3WARNING: invalid cull parm 'front' in shader 'textures/tub/sn_rail1t'
stitched 0 LoD cracks
...loaded 6730 faces, 544 meshes, 360 trisurfs, 0 flares
Corrupt JPEG data: bad Huffman code
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- Server Shutdown (Server fatal crashed: Unsupported marker type 0x97
) -----
==== ShutdownGame ====
---------------------------
Sys_Error: Unsupported marker type 0x97

Shutdown tty console

```

I'm running the game without compiz and I have openGL enabled on my machine. Any help ironing out this bug?

---

