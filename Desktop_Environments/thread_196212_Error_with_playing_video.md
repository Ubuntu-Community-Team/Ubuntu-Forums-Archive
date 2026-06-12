---
title: "Error with playing video"
date: 2006-06-13
forum: Desktop Environments
---

### Post by aanderse on 2006-06-13
Hi,

  I am really hoping I can get some help with this error ...

  I have a 64 bit machine and have had it for about 1 year.  I have been using ubuntu as my regular desktop since 5.10 and enjoying it quite a bit.  At any given time I have 3 operating systems installed (ubuntu64, fedora64, and windows xp32).  Now that you know my system that clears up any questions that were bound to be asked about versions.

  When in ubuntu 5.10 64bit all videos worked great in VLC media player.  I bought a new monitor (acer AL2016W 20 inch widescreen) and then installed dapper64 bit.  I tried to play a video after installing all the correct plugins and got an error much like this :

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 35 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


  I was concerned.  So I booted up fedora core 5 64bit and installed VLC media player ... do my discontent I received the exact same type of error.  I originally assumed this be some sort of a weird 64bit bug I had run into.  I then installed 32bit dapper tonight and to my astonished horror ... again, I received the exact same type of error.

  This leads me to the clear assumption that it is infact a problem with my monitor being incompatible with linux in some way.  Note that videos still play fine in windows.

  If anyone can offer me any help it would be greatly appreciated.

  Thanks,
  aanderse

[EDIT] I get the same error from using either totem or VLC

---

### Post by Amaranth on 2006-06-13
Your monitor has nothing to do with it. It almost sounds like you're using XGL.

---

### Post by aanderse on 2006-06-13
I am using a standard installation of ubuntu 32bit currently, dapper drake, gnome.

---

### Post by aanderse on 2006-06-15
bump ^_^

---

### Post by ions on 2006-12-25
I'm not so sure the monitor has nothing to do with it.  Although how it has something to do with it is beyond me BUT I just got this thing to display the proper resolution (1680x1050) and now video crashes.

Here is the mplayer output: 

```
$ mplayer 1012\ -\ Go\ God\ Go-notv_mrtwig.net.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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
Playing 1012 - Go God Go-notv_mrtwig.net.avi.
AVI file format detected.
VIDEO:  [XVID]  512x384  24bpp  23.976 fps  986.4 kbps (120.4 kbyte/s)
Clip info:
 Software: transcode-1.0.2
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
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'NVidia'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
alsa-init: playback open error: No such device
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 512 x 384 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 512x384 => 512x384 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
chris@tolstoy:~/Desktop/Video/TV/SouthPark DivX TVrip 1012-1014$

```

---

