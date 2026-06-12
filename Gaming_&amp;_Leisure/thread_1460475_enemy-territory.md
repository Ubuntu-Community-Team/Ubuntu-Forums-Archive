---
title: "enemy-territory"
date: 2010-04-22
forum: Gaming &amp; Leisure
---

### Post by grim340 on 2010-04-22
i installed enemy-territory from playdeb.net.
when i try to run it i get a blank screen with a dialog box
that say "res out of range" or sumthing like that.  :confused:

i have alien-arena, open-arena. 
and they work great.

---

### Post by grim340 on 2010-04-22
here i what i get when i run sudo lshw -C video:
```

*-display               
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)

```

---

### Post by grim340 on 2010-04-22
i have the proprietary driver version 185 (recommended) installed.
it's running according to System-Administration-Hardware Drivers

---

### Post by grim340 on 2010-04-22
i checked for updates and found/installed alien-arena updates.
now alien-arena fails to start.
here is what i get:
```

using /home/.../.alien-arena/data1/ for writing
using /home/.../.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
execing config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy


```

---

### Post by sunu mishra on 2010-04-22
is that a good game???:popcorn:

---

### Post by grim340 on 2010-04-22
it's old, but it's alright.

---

### Post by grim340 on 2010-04-22
the dialog get on the blank screen says
Input out of range change settings to 1366x768 60Hz.

i went into my Nivida settings in 
(System-Aministration-Nvidia X ServerSetings)
and i do not have 1366x768 but i do have 1368x768.

so i tried and that does not work either.
HELP :confused:

---

### Post by Bölvaður on 2010-04-22
> **grim340 said:**
> 
when i try to run it i get a blank screen with a dialog box
that say "res out of range" or sumthing like that.  :confused:


sounds like a problem I had. Go find the config file in your home folder. press ctrl+H to find it as the config files for et is hidden. Look for how to change video to 800x600.
If that doesn't do anything then try other resolutions.,... and then give up and try to do something that isn't _this_ silly

---

### Post by grim340 on 2010-04-22
well i found ~./etwolf/etmain/etconfig.cfg

---

### Post by grim340 on 2010-04-23
that did not work

---

### Post by grim340 on 2010-04-23
i downloaded and installed urbanterror from playdeb.net
this i what i get after i hit esc to get out of the blank screen
```

ioQ3 1.35urt linux-x86_64 Aug 11 2009
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
GL_RENDERER: GeForce 6150SE nForce 430/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6150SE nForce 430/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 185.18.36
GL_MAX_TEXTURE_SIZE: 4096
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
0x3316d90 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
total 0, hsize 1021, zero 1021, min 0, max 0
total 9314, hsize 1021, zero 1, min 0, max 28
VM file ui compiled to 3009608 bytes of code (0x7fe51d76e000 - 0x7fe51da4cc48)
compilation took 1.522950 seconds
ui loaded in 33931488 bytes on the hunk
UI menu load time = 244 milli seconds
UI menu load time = 191 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ...-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Shutdown tty console


```

right now the only game that still works is open-arena.
errrrrrrrrrrr

---

