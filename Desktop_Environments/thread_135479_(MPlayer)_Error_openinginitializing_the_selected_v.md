---
title: "(MPlayer) Error opening/initializing the selected video_out (-vo) device."
date: 2006-02-23
forum: Desktop Environments
---

### Post by dantheman on 2006-02-23
I've had some MASSIVE problems with MPlayer and Ubuntu so far. The first was installing it... I finally found a .deb for mplayer and downloaded all the dependencies and finally got it to work. Now for some reason... it can't find a video output device to play the video (audio is ok). 

```
mplayer -vo help
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 8, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Warning unknown option vo_driver at line 4
Available video output drivers:
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        vesa    VESA VBE 2.0 video output
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```

These are the devices listed... I tried all of them and the only one that works is "vesa" but it will play the video FULLSCREEN and then you can't get back into XWindows after the video is done (just displays random colors and bars and you are forced to hard-reboot). 

Any help? 

My video card is an ATI Radeon 9200SE and my monitor is a Benq FP731. 

-Dan-

---

### Post by dantheman on 2006-02-24
Does no one else use MPlayer? Did you retrofit Totem to play mpegs? Do I have to reinstall MPlayer and use a special ./configure --enable (something) to make it work with my video card?

---

### Post by florizs on 2006-03-04
I have the same problem, it's something with the fglrx driver I believe.
have you tried this thread? it didn't work for me but maybe it helps you

[http://www.ubuntuforums.org/showthread.php?t=137560&highlight=mplayer+video_out](http://www.ubuntuforums.org/showthread.php?t=137560&highlight=mplayer+video_out)

---

