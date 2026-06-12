---
title: "Troubles installing Warsow"
date: 2006-11-05
forum: Gaming &amp; Leisure
---

### Post by Super King on 2006-11-05
I'm trying to install the [Warsow]("http://www.warsow.net") FPS on Ubuntu Edgy, but am running into problems. After I extract the stuff from the tar.gz download, I run the warsow shell script. This is the error I'm getting when running it from the terminal:

```
my@comp:~/Desktop/warsow$ ./warsow
Added pk3 file ./basewsw/data0.pk3 (215 files)
Added pk3 file ./basewsw/data0pure.pk3 (647 files)
Added pk3 file ./basewsw/data1.pk3 (2 files)
Added pk3 file ./basewsw/data1pure.pk3 (15 files)
Added pk3 file ./basewsw/map_wctf1.pk3 (43 files)
Added pk3 file ./basewsw/map_wctf2.pk3 (44 files)
Added pk3 file ./basewsw/map_wdm1.pk3 (37 files)
Added pk3 file ./basewsw/map_wdm2.pk3 (57 files)
Added pk3 file ./basewsw/map_wdm3.pk3 (57 files)
Added pk3 file ./basewsw/map_wdm5.pk3 (102 files)
Added pk3 file ./basewsw/map_wdm6.pk3 (23 files)
Added pk3 file ./basewsw/map_wmid1.pk3 (25 files)
Added pk3 file ./basewsw/map_wmid2.pk3 (6 files)
Added pk3 file ./basewsw/map_wmid3.pk3 (15 files)
Added pk3 file ./basewsw/map_wrace1.pk3 (14 files)
Added pk3 file ./basewsw/map_wtest13.pk3 (62 files)
Added pk3 file ./basewsw/map_wtest4.pk3 (96 files)
Added pk3 file ./basewsw/map_wtest7.pk3 (34 files)
Added pk3 file ./basewsw/modules_02.pk3 (12 files)
Added pk3 file ./basewsw/modules_021.pk3 (15 files)
Using . for writing
Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
Game running at 62 fps. Server transmit at 20 pps
Console initialized.
------- sound initialization -------
Loading sound module: openal
Loading OpenAL library: libopenal.so.0
Failed to load OpenAL library: libopenal.so.0
Initialization of openal failed
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 940
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 940
Channels: 2

WARNING: sdlmixsamps wasn't a power of two (7520), so we made it one (4096).
Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

----- R_Init -----
ref_gl version: GL 0.01
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 24, depthbits 24, stencilbits 0
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 16, depthbits 16, stencilbits 0
..Error couldn't set GLX visual
********************
ERROR: Failed to load libGL.so.1
********************
Error: Failed to load libGL.so.1
Received signal 11, exiting...

```

Looks like something with OpenGL. I've tried looking for relevant packages in Synaptic but haven't found any that I think would do the trick. I'm using the generic nvidia driver if it matters. Thanks for any suggestions/solutions.

---

### Post by Perfect Storm on 2006-11-05
Have you install 3D acc. driver for your card?

---

### Post by Super King on 2006-11-05
Hmm, how would I check for that?

---

