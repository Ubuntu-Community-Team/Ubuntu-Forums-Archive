---
title: "MPlayer cache option"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Nannygoat on 2006-07-08
Hi folks,

I'll appreciate some help with the following problem: I've mounted a samba drive so I would be able to play netwotk streams in MPlayer. The only way to get a fluent performance is to enable the cache option in preferences. So far so good but the issue is that MPlayer doesn't remember this particular choice of mine. The next time I start MPlayer the cache option is unticked again. I know I could use the console instead but I insist using the GUI. Any ideas how to "remember" the cache option? I checked the configuration file (the GUI one) in .mplayer - it says cache=yes and next time  start MPlayer it displays "no". Any suggestions? Thanks in advance!

---

### Post by zerwas on 2006-07-08
Go edit the systemwide config-file of mplayer:
```
sudo gedit /etc/mplayer/mplayer.conf
```
and look for the cache option.

I hope this might help.

Greetings,
zerwas

---

### Post by Nannygoat on 2006-07-08
zerwas, thanks for the suggestion but mplayer "resets" the cache value in the config file every time it starts...maybe it's some kind of bug or something.

---

### Post by zerwas on 2006-07-08
But mplayer is **not** able to reset the file in /etc/mplayer.
Hmm, my next idea would be to simply change the rights of the .mplayer/config file.
```

sudo chown root:root /home/nannygoat/.mplayer/config
```

Or, another option, that "solves" the problem, could be to do this:
[LIST=1]
[*]```
sudo mv /usr/bin/gmplayer /usr/bin/gmplayer.standard
```
[*]sudo gedit /usr/bin/gmplayer
[*]Enter this line now:
```
#/bin/bash
/usr/bin/gmplayer.standard -cache 10000 $1
```and save the file and exit the editor
[*]make the "new" gmplayer file executable: sudo chmod +x /usr/bin/gmplayer
[/LIST]
You can edit the -cache value in step 3 to your wishes.
It is really no *good* option perhaps, but it works here.

Greetings,
zerwas

---

### Post by Nannygoat on 2006-07-08
I can't blame noone but myself. Your first advice helped me a lot, I guess I wasn't paying enough atention :lol: Chears, mate, everything's OK now!

---

### Post by citizenr on 2006-07-08
I have another gmplayer problem, it ignores my /.mplayer/input.conf :/ it doesnt even read it

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
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
Playing /media/torrenty/Dream Child/The Dream Child.avi.
AVI file format detected.
VIDEO:  [DX50]  760x576  12bpp  25.000 fps  1164.2 kbps (142.1 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 760 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.32:1 - prescaling to correct movie aspect.
VO: [xv] 760x576 => 760x576 Planar YV12  [fs]
[mpeg4 @ 0x86fd3e8]frame skip 8t:  0.000   1/  1 ??% ??% ??,?% 0 0
[mpeg4 @ 0x86fd3e8]frame skip 8t:  0.004   2/  2 ??% ??% ??,?% 0 0
[mpeg4 @ 0x86fd3e8]frame skip 8t:  0.008   3/  3 ??% ??% ??,?% 0 0
alsa-space: xrun of at least 256.128 msecs. resetting stream1.3% 0 0
alsa-uninit: pcm closed-0.002 ct:  0.256 2982/2982 12%  5%  1.2% 7 0

Exiting... (Quit)


i binded smaller seks to mouse roll and it keeps ignoring this file :/
 worst yey i cant for the love of my cat find a way in Ubuntu to EDIT "open with" mime types and associated programs. I can Add new, remove, but not edit :/ so flustrating.

---

### Post by zerwas on 2006-07-08
No problem mate ;-).
And it's also the best solution you could do.

have a nice weekend,
zerwas

---

### Post by zerwas on 2006-07-08
@citizenr:

Try to set the options in the file systemwide input.conf
```

sudo gedit /etc/mplayer/input.conf
```

---

### Post by citizenr on 2006-07-09
> **zerwas said:**
> @citizenr:

Try to set the options in the file systemwide input.conf
```

sudo gedit /etc/mplayer/input.conf
```

no luck, there are no binds to mouse buttons in that file yet gmplayer has some, looks like someone hardcoded input.cfs into gmplayer :(

[email]rasz@rasz-desktop:~/.mpla[/email]yer$ gmplayer -input input.conf
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.



Option input: Unknown suboption input.conf
91 audio & 204 video codecs

there is no -input parameter either :/

---

