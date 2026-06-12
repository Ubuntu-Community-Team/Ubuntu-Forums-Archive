---
title: "Enhanced Podcast m4a/mp4"
date: 2006-09-09
forum: Desktop Environments
---

### Post by bluenova on 2006-09-09
Hi guys and gals,

I am trying to play an enhanced podcast. The only program I can get to run it is mplayer (cli). Running it from the command line is fine, but if I try to run it with gmplayer it starts for a second then crashes, here is the output:
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/bluenova/.ipodder/downloads/Best of Moyles Enhanced/bestofmoylesenhanced_20060908-0815_40_pc.m4a.
ISO: File Type Major Brand: Apple iTunes AAC-LC Audio
Quicktime/MOV file format detected.
--------------
MOV track #0: 15 chunks, 15 samples
Generic track - not completely understood! (id: 0)
--------------
MOV track #1: 7 chunks, 7 samples
Generic track - not completely understood! (id: 1)
--------------
MOV track #2: 8302 chunks, 77525 samples
Audio bits: 16  chans: 2  rate: 44100
MOV: Found MPEG4 audio Elementary Stream Descriptor atom (51)!
Fourcc: mp4a
--------------
MOV track #3: 14 chunks, 14 samples
Image size: 300 x 300 (24 bpp)
Display size: 160 x 160
Fourcc: jpeg  Codec: ''
--------------
MOV: longest streams: A: #2 (77525 samples)  V: #3 (14 samples)
VIDEO:  [jpeg]  300x300  24bpp  0.009 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 300 x 300 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is 1.00:1 - prescaling to correct movie aspect.
VO: [x11] 300x300 => 300x300 Planar YV12
Shared memory not supported
Reverting to normal Xlib
[ws] Error in display.
[ws]  Error code: 8 ( BadMatch (invalid parameter attributes) )
[ws]  Request code: 73
[ws]  Minor code: 0
[ws]  Modules: decode_video

```

I thought that gmplayer uses mplayer to do its work, so why would it run in mplayer but not gmplayer?

Also does anyone know of a podcast manager that supports any player. Ipodder seems nice, but for some crazy reason the only media player options are XMMS or nothing (you can even select XMMS or Nothing).

---

### Post by Junx on 2006-09-09
Check your version of mplayer and gmplayer; if they're different, there's a problem.

---

