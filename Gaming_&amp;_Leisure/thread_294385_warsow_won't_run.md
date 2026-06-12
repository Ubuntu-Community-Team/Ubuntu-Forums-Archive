---
title: "warsow won't run"
date: 2006-11-06
forum: Gaming &amp; Leisure
---

### Post by juanej on 2006-11-06
Everytime i try to run warsow i get this:

[sis_alloc.c:186]:Failure to allocate back buffer.

I have a sis 630 with the winischhofer drivers

---

### Post by TheRingmaster on 2007-01-14
I can't get warsow to work either.
when I try to run it in the terminal I get this output: > petey@petey-desktop:~$ cd ~/Desktop/warsow
petey@petey-desktop:~/Desktop/warsow$ ./warsow
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
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

----- R_Init -----
ref_gl version: GL 0.01
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..Got colorbits 24, depthbits 24, stencilbits 0
800x600 -> 1280x1024: 424
800x600 -> 1024x768: 168
800x600 -> 800x600: 0
800x600 selected
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  17 (XF86VidModeGetGammaRamp)
  Value in failed request:  0x2e00004
  Serial number of failed request:  48
  Current serial number in output stream:  48


---

### Post by haxer on 2007-01-14
do you have installed drivers?:-k

Using . for writing
Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
Game running at 62 fps. Server transmit at 20 pps

---

