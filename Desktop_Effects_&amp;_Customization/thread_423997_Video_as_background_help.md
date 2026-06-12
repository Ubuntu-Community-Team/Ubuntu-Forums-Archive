---
title: "Video as background help"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by wconstantine on 2007-04-26
Video as background is a very neat thing aswell! Anyone got an idea how to do it? I've tried mplayer with the command:
mplayer -rootwin video.avi but it didn't work. It gave me the following message:

viljam@revelations:~/Desktop/essential-20061022$ mplayer -rootwin /media/sdb3/Filmer/Coral_Reef_Adventure_1080.wmv 
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/sdb3/Filmer/Coral_Reef_Adventure_1080.wmv.
ASF file format detected.
VIDEO:  [WMV3]  1440x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:1.0".
Xv: could not grab port 48
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Creating new registry
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:4665600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1440 x 1080 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1440x1080 => 1440x1080 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
GetOutput r=0x0   size:73728  align:1
StreamCount r=0x0  1  1
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:  22.3 V:  22.4 A-V: -0.136 ct:  0.229 439/439 31%  3%  2.4% 0 0 


It's worth mentioning that the counter down there just ticks up and down as it really was playing something. I've tried with downloading the binary codecs as it says aswell. Then I only could here the sound. I run gnome + xgl + beryl.

---

### Post by Xeora on 2007-04-26
Xwinwrap - try it...

---

### Post by wconstantine on 2007-04-26
Thanks m8. It worked fine! Although it draws CPU as hell, but why not. I got more than enough anyways.

---

### Post by jrock2004 on 2007-04-26
just a little off topic but why in the heck would you want a video playing in your backround

---

### Post by en3rgy on 2007-04-26
> **jrock2004 said:**
> just a little off topic but why in the heck would you want a video playing in your backround
Imagine a picture of a wheat swaying to a gentle breeze. Now imagine that same video as your desktop background. Decrease stress, improve productivity and just look really cool. That's what GUI is all about.

---

### Post by altaaa on 2007-04-26
Does anyone know where to download such (short/looped) videos?

---

### Post by wconstantine on 2007-04-26
Well I fetched some HD movies from Microsofts own website... They were not so good but something already.

Or as another example: imagine someone flying among the clouds high up in the air or maybe a tropical beach with waves coming against you all the time. It's just wonderful. If you find any good movies please link!

---

### Post by altaaa on 2007-04-27
Too bad, I couldn't get xwinwrap to work properly with AIGLX :(

---

### Post by Aetherius on 2007-04-27
where on microsofts site did you get the videos?

---

### Post by wconstantine on 2007-04-27
> **Aetherius said:**
> where on microsofts site did you get the videos?

[http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx](http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx)

---

