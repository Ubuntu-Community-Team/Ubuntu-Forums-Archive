---
title: "warsow"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by wolf414 on 2006-06-04
I installed warsow but when i try to run it i get this

```
chris@chris-desktop:~/warsow$ sh warsow
Added pk3 file ./basewsw/data0.pk3 (884 files)
Added pk3 file ./basewsw/map_wctf1.pk3 (19 files)
Added pk3 file ./basewsw/map_wtest1.pk3 (58 files)
Added pk3 file ./basewsw/map_wtest3.pk3 (31 files)
Added pk3 file ./basewsw/map_wtest4.pk3 (89 files)
Added pk3 file ./basewsw/map_wdm1.pk3 (35 files)
Added pk3 file ./basewsw/map_wdm2.pk3 (53 files)
Added pk3 file ./basewsw/map_wdm5.pk3 (97 files)
Added pk3 file ./basewsw/map_wmid1.pk3 (21 files)
Added pk3 file ./basewsw/map_wmid2.pk3 (2 files)
Added pk3 file ./basewsw/map_wmid3.pk3 (13 files)
Using /home/chris/.warsow/basewsw for writing
Unknown command "snd_restart"
Unknown command "in_restart"
execing default.cfg
Line has unmatched quote, discarded.
couldn't exec config.cfg
couldn't exec autoexec.cfg
fs_usehomedir is write protected.
Server running at 20 pps
Console initialized.

------- sound initialization -------
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 22050
Samples: 470
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 22050
Samples: 470
Channels: 2

WARNING: sdlmixsamps wasn't a power of two (3760), so we made it one (2048).
Starting SDL audio callback...
SDL audio initialized.
LoadLibrary (libvorbisfile.so):(libvorbisfile.so: cannot open shared object file: No such file or directory)
sound sampling rate: 22050
------------------------------------

----- R_Init -----
ref_gl version: GL 0.01
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..Got colorbits 24, depthbits 24, stencilbits 0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  23
  Current serial number in output stream:  26
chris@chris-desktop:~/warsow$

```

Can anyone help me?

---

### Post by homerhomer on 2006-06-05
Hey, I was running the game earlier and it's great.  It looks like you don't have GLX configured correctly, go to the command prompt and run the following

glxinfo | grep direct

you should get a direct rendering = Yes

if not you need to properly setup your video card

---

