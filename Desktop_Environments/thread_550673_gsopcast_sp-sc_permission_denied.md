---
title: "gsopcast sp-sc permission denied"
date: 2007-09-14
forum: Desktop Environments
---

### Post by steveeeeeeeee on 2007-09-14
I'm relatively new, so forgive me if I'm not clear.

Attempted to install gsopcast, application appears fine, the channel list appears and I can select channels but the channel never appears. 

In the terminal I get a continous message "sp-sc permission denied". 

Here is some code showing the permission of the files, which I changed so they'd be available to everyone, and also me attempting to use gsopcast.

```
stephen@stephen-desktop:/usr/local/bin/sp-sc$ ls -l
total 3716
-rw-r--r-- 1 stephen stephen     572 2006-11-28 07:17 Readme
-rwxrwxrwx 1 stephen stephen  828708 2007-07-09 08:44 sp-sc-auth
-rwxrwxrwx 1 stephen stephen  833168 2007-07-09 08:44 sp-so-auth
-rw-r--r-- 1 stephen stephen 2119078 2007-07-09 08:46 vlc-install-utf8-pid-getport.tgz

stephen@stephen-desktop:/usr/local/bin/sp-sc$ gsopcast
GTK Accessibility Module initialized
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied
sp-sc: Permission denied

```

Can anybody suggest anything?

---

### Post by pt123 on 2007-09-15
have you set player in the config
```


mplayer -ontop -geometry 100%:100%

```

---

### Post by steveeeeeeeee on 2007-09-15
Thanks you for replying pt123. Yes, the config player settings are 

mplayer -ontop -geometry 100%:100%

So, the problem must be something else...

---

### Post by pt123 on 2007-09-15
you dont have problems with mplayer from the terminal?

look at this thread
[http://ubuntuforums.org/showthread.php?p=3368773](http://ubuntuforums.org/showthread.php?p=3368773)

did you install it from a deb

---

### Post by steveeeeeeeee on 2007-09-15
mplayer seems to work fine from the terminal. I installed from deb, yes. I've installed various versions from 1.2.1

```
stephen@stephen-desktop:~$ mplayer '/home/stephen/Examples/Experience ubuntu.ogg'
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/stephen/Examples/Experience ubuntu.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  360x288  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x8939638]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 360 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
VO: [xv] 360x288 => 360x288 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 45.3 kbit/6.42% (ratio: 5666->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:  37.6 V:  37.6 A-V: -0.003 ct: -0.018 941/941  6%  1%  1.4% 0 0 
Exiting... (Quit)

```

I think the problem is with sp-sc, when I try to use the terminal and type "sp-sc" it says command not found.

Okay, I've just reinstalled sp-sc onto my desktop, unpacked it and it runs fine from terminal, I just need to get gsopcast working...

---

