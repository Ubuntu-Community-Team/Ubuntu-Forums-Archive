---
title: "Sound/Video Skipping"
date: 2006-06-10
forum: Desktop Environments
---

### Post by XVampireX on 2006-06-10
Hi, I installed ubuntu dapper a few days ago. But I'm having some problems with sound. Most of the time it works fine, playing music in players works fine. But here comes the problem:

Everytime I try to view a movie (Especially with mplayer), I get xruns (When it occures, the video skips). Well, someone on IRC in the channel told me to use -framedrop, it somewhat worked (There's still some skips.... sometimes, not always).

Ok, next is problem with a game called StepMania, everytime I play it, it skips during gameplay and even before gameplay. I have no idea why it happens. I've tried a few native games (from the repositories) and most of them have lag, too.

My PC specs are:
1.5GHz, 256MB Ram (RDRam), 128MB Video Ram, Sound Blaster PCI 128.

The thing is, with these specs, everything worked just fine when I was on windows.

Can anyone please help me?
If anything, I think the problem is with the frame buffer (I used kubuntu before ubuntu, and I knew how to set the frame buffer higher, but here there's nothing like that in the system tools).

---

### Post by blackjack6.21.91 on 2006-06-10
In mplayer, make sure your using xv as your video driver.  I have the same problem with games, though.  But wow are the native ones great!  Esp.  Kobo Deluxe rofl.

Fish and bumps,
blackjack

---

### Post by XVampireX on 2006-06-10
I was using it all along... but take a look at this:

> serge@serge-desktop:~/Anime$ mplayer -framedrop \[DB\]_Naruto_188_\[C75E7923\].avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4 Willamette; Xeon Foster (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing [DB]_Naruto_188_[C75E7923].avi.
AVI file format detected.
AVI: ODML: Building odml index (2 superindexchunks)
VIDEO:  [XVID]  640x480  12bpp  23.976 fps  898.0 kbps (109.6 kbyte/s)
Clip info:
 Software: Windows Movie Maker 2.1
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12
alsa-play: xrun of at least 0.008 msecs. resetting stream 1.5% 17 0
A:  73.2 V:  73.2 A-V: -0.002 ct: -0.037 1755/1755 14%  0%  1.5% 21 0

---

### Post by DarkMageZ on 2006-06-12
i believe i can replicate your stepmania issue, but not the mplayer, are u by any chance an ati user? cause the other user with this issue with stepmania is an ati user as well.

---

