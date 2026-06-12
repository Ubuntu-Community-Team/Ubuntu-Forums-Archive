---
title: "Still Haven't Figured Out My DVD Problem."
date: 2005-07-20
forum: Desktop Environments
---

### Post by jlacroix on 2005-07-20
Hello everyone, I reinstalled Ubuntu and I still have the same problem playing DVD's. I installed Ubuntu on my wife's computer and she is having the same problems. Before I continue, yes, I do have libdvdcss installed.

Computer:
AMD Athlon 900mhz
768MB Ram
Gefore Fx5500 256MB (NVidia driver installed)
Surround sound Creative Soundblaster, using Alsa. (Tried all other audio plugins).
Ubuntu Hoary

Basically, my DVD's crash, each at different points. The points that the DVD's crash at, it will crash at the exact same point every single time you play the DVD. You can set your watch to it.

I am using Totem-xine (I also tried Xine) and I get an error message "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

If I use MPlayer, it will crash right when initializing the DVD, and that happens with all DVD's. I get "Mplayer interrupted by signal 11in module decode_audio".

If I use regular Xine, I get "The audio device is unavailable. Please verify if another program already use it."

I've tried this with and without DMA support being turned on. Same problem with both.

Terminal output:

```

jeremy@Athlon:~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0008a79d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0008ee8c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0008ee9d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000df13d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000df14e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000fa283
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001033ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0038b8c6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0038b8d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0038f1bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0038f1d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00397633
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00397644
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00399f2a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00399f3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0039fb36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0039fb47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003a9c12
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003a9c23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003b612c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003b613d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003bc90c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003bc91d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003c1592
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003c15a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003c4d08
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003c4d19
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003e1fd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003e1fea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003f4f08
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003f4f19
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
jeremy@Athlon:~$

```

PLEASE help. Ubuntu is the only distro I am having this problem with.

---

### Post by amohanty on 2005-07-21
Try installing libdvdcss2

AM

---

### Post by jlacroix on 2005-07-21
That's the first thing I did. :(

---

