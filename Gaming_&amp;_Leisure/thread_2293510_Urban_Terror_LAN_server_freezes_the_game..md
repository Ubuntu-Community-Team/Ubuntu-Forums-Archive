---
title: "Urban Terror LAN server freezes the game."
date: 2015-09-05
forum: Gaming &amp; Leisure
---

### Post by mina2 on 2015-09-05
Hi!

I'm on Ubuntu 14.04. I can't start a LAN server on Urban Terror 4.2

Whenever I hit "Start Server" the game just freezes. Even the audio freezes.

I tried starting the game from terminal but it doesn't give out any errors.

Here's a screenshot of the settings

[ATTACH=CONFIG]264245[/ATTACH]

and here's part of the terminal output:

```
22249 files in pk3 files
execing default.cfg
"MINUS" isn't a valid key
"PLUS" isn't a valid key
execing q3config.cfg
couldn't exec autoexec.cfg
Minimum com_hunkMegs is 512, allocating 512 megs.
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
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce GTX 770/PCIe/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic


GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce GTX 770/PCIe/SSE2
GL_VERSION: 4.4.0 NVIDIA 340.76
GL_MAX_TEXTURE_SIZE: 16384
GL_MAX_ACTIVE_TEXTURES_ARB: 4


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
XF86VidModeSetGamma: 1.200, 1.200, 1.200.
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


dmaHD 3D software sound engine by p5yc0runn3r
 dmaHD full 3D sound mixer [10]
 2 ch / 22050 Hz / 16 bps
 No sounds loaded yet.


Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
total 0, hsize 1021, zero 1021, min 0, max 0
total 10360, hsize 1021, zero 0, min 1, max 28
VM file ui compiled to 3527231 bytes of code (0x7ffb1ed61000 - 0x7ffb1f0be23f)
compilation took 0.447431 seconds
ui loaded in 17222880 bytes on the hunk
UI menu load time = 419 milli seconds
UI menu load time = 76 milli seconds
16 bots parsed
14 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: 4sq
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
XF86VidModeSetGamma: 1.200, 1.200, 1.200.
------ Urban Terror Auth System ------
auth: resolving authserver address 
auth: resolved 
auth: sending authorize request for your key (try 1).
--------------------------------------
auth: validated - account: 842mono - notoriety: basic (10)
Missing { in info file
95 arenas parsed

```

...I made a question on askubuntu before but I got nothing, so here it is: [http://askubuntu.com/questions/631411/cannot-start-an-urban-terror-lan-server-game-hangs-and-i-have-to-restart-pc](http://askubuntu.com/questions/631411/cannot-start-an-urban-terror-lan-server-game-hangs-and-i-have-to-restart-pc)

any ideas?

---

