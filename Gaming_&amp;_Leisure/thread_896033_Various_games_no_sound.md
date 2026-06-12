---
title: "Various games no sound"
date: 2008-08-20
forum: Gaming &amp; Leisure
---

### Post by billybag on 2008-08-20
I know sound has been a big issue recently, especially since pulseaudio has been implemented. Every so often i run into no sound problems with various games and then i just give up trying to fix it and just get rid of the game. However, I am really interested in Digital Paintball 2 and Legends and would really like to get the sound to work for this one.

Has anyone had any luck fixing sounds to work with games?

Paintball 2 tells me it could not load /dev/dsp

```
------- sound initialization -------
LoadLibrary("./snd_oss.so")
dlopen("q2a3d.so") failed: q2a3d.so: cannot open shared object file: No such file or directory
Error loading up q2a3d module.
------------------------------------
------- Loading ref_pbgl.so -------
LoadLibrary("./ref_pbgl.so")
ref_gl version: PB2GL 0.22
Using libGL.so for OpenGL...
Initializing OpenGL display
...setting mode 18: 1280 768
Using XFree86-VidModeExtension Version 2.2
I got 8 bits of red
I got 8 bits of blue
I got 8 bits of green
I got 24 bits of depth
I got 8 bits of alpha
I got 8 bits of stencil
Using hardware gamma
------------------------------------
====== Paintball II Initialized ======

70.85.9.178:27900: vninitresponse
70.85.9.178:27900: vnresponse

------- sound initialization -------
LoadLibrary("./snd_oss.so")
/dev/dsp: Device or resource busy
SNDDMA_Init: Could not open /dev/dsp.

------- sound initialization -------
LoadLibrary("./snd_oss.so")
dlopen("q2a3d.so") failed: q2a3d.so: cannot open shared object file: No such file or directory
Error loading up q2a3d module.
Cmd_AddCommand: play already defined
Cmd_AddCommand: stopsound already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
------------------------------------
recursive shutdown

```

---

