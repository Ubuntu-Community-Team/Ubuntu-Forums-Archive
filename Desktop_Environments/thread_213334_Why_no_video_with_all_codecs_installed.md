---
title: "Why no video with all codecs installed?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by MartynM on 2006-07-11
I could use some help regarding getting AVIs and mpegs to play in any of the players I have installed, VLC, Movie player, Totem etc. I (to the best of my limited knowlege) have all the relavent codecs installed, I've run EasyUbuntu, Automatix, and followed as many threads in this forum as possible, but still can't get anything at all to play.
I am running an ATI Radeon 9100 on the ubuntu ATI driver not the fglrx one, I installed that in a previous ubuntu install and didn't have a lot of success with it. I gather that there is a problem with Radeon 9100s and the fglrx, is this true? Can I run AVIs on the stock ATI driver as it's not 3D?

I'm resisting the tempteation to just get another graphics card, and as everything else is running so well (graphicswise) I'm even wondering if the driver is the problem. Does it have any bearing on simple video playback? 

BTW, DVDs don't playback either, I get sound and even active (clickable) menu hotspots on the blank screen, but no picture.

Any ideas?

Cheers

M

---

### Post by Thund3rstruck on 2006-07-11
I have an ATI radeon (i forget the model) in my laptop and I have no issues. Do you have mplayer installed? Are you getting the:

***error initializing playback, no video out (-vo) device***

or something like that?

In any event, follow the [wiki]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs") 
and then let us know if you're working ot not

---

### Post by MartynM on 2006-07-11
> **Thund3rstruck said:**
> I have an ATI radeon (i forget the model) in my laptop and I have no issues. Do you have mplayer installed? Are you getting the:

***error initializing playback, no video out (-vo) device***

or something like that?

In any event, follow the [wiki]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs") 
and then let us know if you're working ot not

Thanx for the reply.

All those codecs are installed, I get no error message and I already followed that guide and a few others. I just ran everything on that page to make sure before posting, and just got confirmation that "*everything* is already the newest version"
 I'm thinking that it really might be a Gcard driver issue, I'm just looking for confirmation that this is the case before screwing around with the fglrx driver again.

Cheers

M

---

### Post by Thund3rstruck on 2006-07-11
You're definatly getting output somewhere (possibly in /var/log/*)... if you have mplayer installed launch an mpg file from the command line

```

mplayer myvideo.mpg

```

Then at least you'll see the error clearly in the terminal and can troubleshoot from there.

---

### Post by MartynM on 2006-07-11
Just gave that a shot and got this;

 > mplayer gass.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
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
Playing gass.avi.
AVI file format detected.
VIDEO:  [dvsd]  720x576  24bpp  25.000 fps  28800.0 kbps (3515.6 kbyte/s)
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Creating new registry
Decoder supports the following YUV formats: YUY2 UYVY
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 576 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x576 => 720x576 Packed YUY2
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/26212 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
A:  36.0 V:  36.0 A-V:  0.036 ct: -0.037 901/901 19%  1%  0.5% 1 0
alsa-uninit: pcm closed

Exiting... (End of file)

I'm not too sure whats meant by this bit at the beginning "Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts."

Pretty new to Linux and I'd like to know what things like that mean before diving in and hacking my startup settings around. Can you tell from that if there might be an easier solutiion to this?

Thanks for the help.

M

---

### Post by MartynM on 2006-07-11
I just installed the ATI driver and fixed the problem.

It's convinced me that it's worth getting a new graphics card though, performance on this 9100 is pretty disappointing.

Ah well, at least I solved the dvd problem.

---

