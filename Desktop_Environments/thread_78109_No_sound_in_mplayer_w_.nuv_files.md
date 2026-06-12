---
title: "No sound in mplayer w/ .nuv files"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dijitao on 2005-10-17
Mplayer isn't detecting any sound in video files in the nuppelvideo (.nuv) file type.  I have taken a nuv file and converted it to an avi file using the tools bundled with dsmyth ([http://dsmyth.sourceforge.net/](http://dsmyth.sourceforge.net/)) and mplayer plays the resulting avi file fine.  Here is the console output from both the .nuv file and the avi file.

**AVI:**
```
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing test.avi.
AVI file format detected.
VIDEO:  [DIVX]  320x240  24bpp  29.970 fps  802.5 kbps (98.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bps)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 320 x 240 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 320x240 => 320x240 Planar YV12
SwScaler: using unscaled Planar YV12 -> BGRA special converter
```

**NUV:**
```
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing test.nuv.
MPEG4-ES file format detected.
FPS seems to be: 302727/10000
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 320 x 240 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 320x240 => 320x240 Planar YV12
SwScaler: using unscaled Planar YV12 -> BGRA special converter

```

---

