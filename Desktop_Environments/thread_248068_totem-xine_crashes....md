---
title: "totem-xine crashes..."
date: 2006-08-31
forum: Desktop Environments
---

### Post by oldforce on 2006-08-31
totem-xine, xine-ui and mplayer crashes when i click to play a .wmv file
here is the console output of totem-xine crash;
```

External func OLEAUT32.dll:8
Called unk_RegOpenKeyA
Called unk_RegQueryValueExA
Called unk_RegCloseKey

```

here is the mplayer console output ;
```

oldforce@oldforce-desktop:~$ gmplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Tualatin (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
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
Playing /home/oldforce/Downloads/axe.wmv.
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000,000 fps    0,0 kbps ( 0,0 kbyte/s)
Clip info:
 name:
 author:
 copyright:
 comments:
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 16000 Hz, 1 ch, s16le, 16,0 kbit/6,25% (ratio: 2000->32000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Called unk_RegOpenKeyA
Called unk_RegQueryValueExA
Called unk_RegCloseKey

```

please tell me what is wrong with my video players...
win32codecs are installed...

---

