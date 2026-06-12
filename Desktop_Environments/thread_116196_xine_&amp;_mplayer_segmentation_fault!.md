---
title: "xine &amp; mplayer: segmentation fault!"
date: 2006-01-12
forum: Desktop Environments
---

### Post by woifi on 2006-01-12
hi!

yesterday i found out, that xine crashes immediately after starting -> segmentation fault (it worked perfectly before). well, i installed mplayer and wow -> it crashes too with segfault!

i've really no idea, so: does anybody have a hint for me?

bye

woifi:

my sys:
breezy bager
athlon 2000+
geforce 2 gts (with nv driver)
```
+++-==============-==============-============================================
ii  mplayer-k7     1.0-pre6-0.3ub transitional dummy package which can be safe
ii  xine-ui        0.99.3-1ubuntu the xine video player, user interface
```

---

### Post by Ampersand on 2006-01-12
Try marking them for complete removal in Synaptic, then installing them again. It's possible that something's wrong with the configuration files. 

Did you change anything before this started happening, or update any software?

---

### Post by Ducino on 2006-01-14
Check if you can run xine or mplayer as root:

sudo xine

If that's the case, you probably have the same problem i had.
fix: chmod a+rx /usr/lib/tls

---

### Post by sinaen on 2006-01-23
i dont think thats the problem i have :(

here is a complete message

sudo mplayer \[YHBT\]_Naruto_167_HDTV_Special_\[76D23E62\].avi
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium M Banias (Family: 6, Stepping: 5)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing [YHBT]_Naruto_167_HDTV_Special_[76D23E62].avi.
AVI file format detected.
AVI: ODML: Building odml index (3 superindexchunks)
VIDEO:  [XVID]  1280x720  16bpp  23.976 fps  1455.4 kbps (177.7 kbyte/s)
Clip info:
 Software: Windows Movie Maker 2.1
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 96.0 kbit/12.50% (ratio: 12000->96000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/1ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/1 channels/2 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 1ch s16le (2 bps)
Building audio filter chain for 48000Hz/1ch/s16le -> 48000Hz/1ch/s16le...
Starting playback...
VDec: vo config request - 1280 x 720 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0 63%


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

---

### Post by tfotherby on 2006-02-15
Note: This command fix's it for me:

sudo touch /etc/ld.so.nohwcap

(see [http://ubuntuforums.org/showthread.php?p=738069#post738069](http://ubuntuforums.org/showthread.php?p=738069#post738069))

---

