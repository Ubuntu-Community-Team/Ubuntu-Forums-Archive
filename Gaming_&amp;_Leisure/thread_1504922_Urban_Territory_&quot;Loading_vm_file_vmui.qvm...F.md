---
title: "Urban Territory &quot;Loading vm file vm/ui.qvm...Failed&quot;"
date: 2010-06-08
forum: Gaming &amp; Leisure
---

### Post by JohnHeikkila on 2010-06-08
Okay, so I have a game called Urban Terror installed on my pc, and it has worked well before.
But this time when I launched the game and tried joining into a server, the game just shut down.
See the console print:
```
joona@Joona-PC:~$ ./UrbanTerror/ioUrbanTerror.i386
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
9483 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Unknown command "/funred"
Unknown command "/funblue"
Minimum com_hunkMegs is 256, allocating 256 megs.
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
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
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 195.36.15
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "pulse".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  256
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
 8192 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xa8153a0 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 352 milli seconds
UI menu load time = 234 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
WARNING: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27961
WARNING: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27962
Hostname: Joona-PC
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
67.202.120.216:27960 resolved to 67.202.120.216:27960
----- FS_Startup -----
Going through search path...

handle 1: music/mainmenu.wav
----------------------
18966 files in pk3 files
Need paks: @q3ut4/zpak000.pk3@q3ut4/zpak000.pk3
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 195.36.15
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
Failed.
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Sys_Error: VM_Create on UI failed
Shutdown tty console
```

I checked the vm/ui.qvm file, and it was there, I haven't touched the file for it has special characters and saving the file may corrupt it.

What could be the problem? Where could I get a new copy of the file without downloading the ~700mb game package again?

---

### Post by JohnHeikkila on 2010-09-07
Got this solved. It was just an corrupted Urban Terror file, in this case the "zpak000_assets.pk3" archive file. I tried to edit it.

Just downloaded UrT again and fixed the files.

---

### Post by zomg007 on 2011-01-05
> **JohnHeikkila said:**
> Okay, so I have a game called Urban Terror installed on my pc, and it has worked well before.
But this time when I launched the game and tried joining into a server, the game just shut down.
See the console print:
```
joona@Joona-PC:~$ ./UrbanTerror/ioUrbanTerror.i386
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
9483 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Unknown command "/funred"
Unknown command "/funblue"
Minimum com_hunkMegs is 256, allocating 256 megs.
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
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
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 195.36.15
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "pulse".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  256
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
 8192 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xa8153a0 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 352 milli seconds
UI menu load time = 234 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
WARNING: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27961
WARNING: UDP_OpenSocket: bind: Address already in use
Opening IP socket: localhost:27962
Hostname: Joona-PC
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
67.202.120.216:27960 resolved to 67.202.120.216:27960
----- FS_Startup -----
Going through search path...

handle 1: music/mainmenu.wav
----------------------
18966 files in pk3 files
Need paks: @q3ut4/zpak000.pk3@q3ut4/zpak000.pk3
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW!
GL_VERSION: 2.1.2 NVIDIA 195.36.15
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
Failed.
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Sys_Error: VM_Create on UI failed
Shutdown tty console
```I checked the vm/ui.qvm file, and it was there, I haven't touched the file for it has special characters and saving the file may corrupt it.

What could be the problem? Where could I get a new copy of the file without downloading the ~700mb game package again?


HOW THE **** DID YOU CHECK THE .qvm FILE???? TELL ME NOW!

---

