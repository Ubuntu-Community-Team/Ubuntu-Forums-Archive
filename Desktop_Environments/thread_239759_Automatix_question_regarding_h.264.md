---
title: "Automatix question regarding h.264"
date: 2006-08-19
forum: Desktop Environments
---

### Post by kpm on 2006-08-19
I can't find a 'post new thread' link anywhere on the Ubuntu Automatix Suport page ([http://ubuntuforums.org/showthread.php?t=203340](http://ubuntuforums.org/showthread.php?t=203340)) so I am posting here...

I just installed Dapper (most excellent!), went to some sites I visited on my old Windows install and realized I had to get the codecs so ran the automatix script (a most helpful and awesome script!) and could then veiw ALMOST all of the streams on the various sites I visit... all but one, which uses Quicktime 7 with the h.264 encoding.  The vids won't play in the browser, and when I try to run them from the terminal I get the following:
```

kmurphy@ranaSylvatica:~$ sudo mplayer
http://onegoodmovemedia.org/movies /0608/ko081806bushismp.mov
Password:
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Te am
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6,
Step ping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing http://onegoodmovemedia.org/movies/0608/ko081806bushismp.mov.
STREAM_HTTP(1), URL:
http://onegoodmovemedia.org/movies/0608/ko081806bus hismp.mov
Resolving onegoodmovemedia.org for AF_INET6...
Couldn't resolve name for AF_INET6: onegoodmovemedia.org
Resolving onegoodmovemedia.org for AF_INET...
Connecting to server onegoodmovemedia.org[208.113.133.167]: 80...
Cache size set to 320 KBytes
Cache fill:  2.79% (9151 bytes)
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
--------------
MOV track #0: 1 chunks, 0 samples
MOV: Found unknown movie atom prjp (12)!
Image size: 320 x 256 (24 bpp)
Display size: 320 x 256
Fourcc: jpeg  Codec: 'Photo - JPEG'
--------------
MOV: longest streams: A: #-1 (0 samples)  V: #0 (1 samples)
VIDEO:  [jpeg]  320x256  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
======================================================================== ==
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
======================================================================== ==
Audio: no sound
Starting playback...
[mjpeg @ 0x86fd3e8]mjpeg: unsupported coding type (c2)
VDec: vo config request - 320 x 256 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)
kmurphy@ranaSylvatica:~$

```

Anyone have any ideas??

Thanks

---

### Post by Tomosaur on 2006-08-19
Automatix has centralised itself since it is now no longer Ubuntu only: 
[http://www.getautomatix.com](http://www.getautomatix.com)

However, this sounds more like a Quicktime problem to me. I'm not up to date on Quicktime support in linux, perhaps you're using an old version or something?

---

