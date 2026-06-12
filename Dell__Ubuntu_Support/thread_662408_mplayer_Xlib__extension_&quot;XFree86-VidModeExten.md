---
title: "mplayer Xlib:  extension &quot;XFree86-VidModeExtension&quot; missing on display &quot;:1.0&quot;."
date: 2008-01-08
forum: Dell  Ubuntu Support
---

### Post by rpglover64 on 2008-01-08
I have an Inspiron 1420 that came with feisty preinstalled.  I upgraded to gutsy and gnome wouldn't load.  I found that I needed to change the xorg.conf file slightly, and gnome started working fine.  Now my problem is that if I try to play something with mplayer, i get this output

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Malcolm in the Middle - 604 - Pearl Harbor.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1001.6 kbps (122.3 kbyte/s)
Clip info:
 Software: VirtualDub
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 

and the movie plays fine; but if I try to play it in fullscreen (either through the -fs  flag by pressing f while it's playing in windowed mode) the output is extremely choppy and it stutters when I try to close it.

The problem seems to be this line:
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

If I use the -display flag to set the display to :0 , it plays fine, but it acts weird (I can't quite describe it).

I have my xorg.conf file attached.

My questions are:
1) how can I fix it so that mplayer plays normally like it did before I upgraded
2) what does that line about xlib mean?

Thank you in advance.

---

