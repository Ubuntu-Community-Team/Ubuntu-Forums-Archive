---
title: "Problems with audio"
date: 2006-06-05
forum: Desktop Environments
---

### Post by drange on 2006-06-05
I'm having some problems with my audio. Nothing comes out of the speaker. I've tried playing .wav, .ogg (vorbis) and .mp3-files, but no sound. I've done this as root and as a regular user. I've tried with both amaroK and mplayer. With mplayer, I get an "permission denied" (look below).

My lspci output:
0000:02:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

It worked on the live CD, but when I installed it, it was gone. I tried cating /dev/urandom to /dev/audio, but first I got a device in use error, then I killed a lot of apps from the `lsof | grep audio'-output, and then it worked, so the hardware is allright, and I believe the drivers work.

I use Kubuntu and I have installed a **LOT** of codecs and programs to get it to work, but nothing's worked.

Any ideas? Do you want an output from lsof?
From mplayer:
```

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
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
Playing 01.Vicarious.mp3.
Audio file file format detected.
Clip info:
 Title: Vicarious
 Artist: Tool
 Album: 10,000 Days
 Year: 2006
 Comment: 
 Track: 1
 Genre: Unknown
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
alsa-uninit: pcm closed0 (07:06.0)  0.7% 

Exiting... (Quit)

```

---

### Post by drange on 2006-06-06
Any ideas?

---

