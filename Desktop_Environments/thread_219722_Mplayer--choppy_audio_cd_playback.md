---
title: "Mplayer--choppy audio cd playback"
date: 2006-07-20
forum: Desktop Environments
---

### Post by antiemptyv on 2006-07-20
I'm using mplayer.  When i play an audio cd using the command

```
mplayer cdda://
```

mplayeropen the cd and begins playing it.  However, The audio playback is interrupted ever few hundred milliseconds.  Here is the output in the terminal:

```

$ mplayer cdda://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6,                                                                                           Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup                                                                                           scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing cdda://.
Found audio CD with 15 tracks.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...

Track 1
alsa-play: xrun of at least 443.398 msecs. resetting stream
alsa-play: xrun of at least 177.873 msecs. resetting stream
alsa-play: xrun of at least 166.183 msecs. resetting stream
alsa-play: xrun of at least 421.917 msecs. resetting stream
alsa-play: xrun of at least 148.328 msecs. resetting stream
alsa-play: xrun of at least 157.895 msecs. resetting stream
alsa-play: xrun of at least 428.331 msecs. resetting stream
A:  13.3 (13.3) of 1715.8 (28:35.8) 34.9% 

MPlayer interrupted by signal 2 in module: decode_audio
alsa-uninit: pcm closed

```

At each of those intervals, the playback stops for a split second, then continues (resets stream) from where it left off.

The funny thing is is that mplayer plays dvds fine, hdparm is set to 'on' and gnome-cd player plays the audio cds fine.  I would prefer to just use mplayer for all my audio/video needs and ditch gnome-cd.

Has anyone run into this problem with mplayer before or know what to do?

Thanks.

edit:  oh, and I tried "Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup"

---

### Post by a212359 on 2006-09-23
I know you had this problem a long time ago...but just in case anyone else has this issue, the solution I've found to work is to increase the cache:

mplayer cdda:// -cache 5000

---

### Post by nantetokuma on 2007-01-22
Thanks for the answer, working fine for me like that!!
really cool to use Mplayer! :D 

[INDENT][SIZE="4"] mplayer -ao alsa -cdrom-device /dev/hdc cdda:// -cache 5000[/SIZE][/INDENT]

dawidbass
on Dapper...

---

