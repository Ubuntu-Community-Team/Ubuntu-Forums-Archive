---
title: "avi files that won't play..."
date: 2006-09-28
forum: Desktop Environments
---

### Post by kpm on 2006-09-28
I am able to view multiple file types in Mplayer and the other standard vid players... But, I have an .avi file (or ten) that Mplayer just runs as jibberish and Totem states tha 'there is no plugin to handle this movie.'  So why is it that one AVI file will play, but others will not??  I have used Automatix to ensure I have all the necessary libraries and plugins, but still no luck.  Does anyone have any ideas??

Thanks

---

### Post by Jussi Kukkonen on 2006-09-28
AVI is just a container format, it can use different codecs.  mplayer probably tells you the codec you need when you try to play the file on the command line.

---

### Post by Monstroxus on 2006-09-28
I have a similar problem, some AVI files play nicely, others just freeze. (a tried a range players, and some just seem to be able to play for 1-2 sec, but then freeze) I have all the codecs installed. Of course when I convert them to MPEG2 or something they play nicely. I especially have problems with captured webcam AVI files. At the other hand, I have a bunch of old Buck Rogers / Star Trek episodes in AVI format and they all play fine.

---

### Post by kpm on 2006-09-28
> **Monstroxus said:**
> "...when I convert them to MPEG2 or something they play nicely."
Thanks for the eresponses.  What do you use to convert video formats??

---

### Post by kpm on 2006-09-28
> **Jussi Kukkonen said:**
> mplayer probably tells you the codec you need when you try to play the file on the command line.
Thanks for the reply.  I pasted the out put below from Mplayer. Seems I don't have a proper audio codec... but also some strange permission error and a complaint about no free x-video port to grab.  I did ensure no other videos or sound were playing... anyway, the avi is just some bad tv show I was trying to use to learn how torrents worked...

```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 6)CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
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
Playing FullHouse1x00-PilotUnairedPilot.avi.
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Xv: could not grab port 65
Could not find free Xvideo port - maybe another process is already using it.
Close all video applications, and try again. If that does not help,
see 'mplayer -vo help' for other (non-xv) video out drivers.
SDL: Using driver: x11
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [sdl] 720x480 => 720x480 Packed YUY2
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Audio: no sound
Starting playback...
V:  67.8 2033/2033 39% 185%  0.0% 0 0

Exiting... (End of file)

```

---

