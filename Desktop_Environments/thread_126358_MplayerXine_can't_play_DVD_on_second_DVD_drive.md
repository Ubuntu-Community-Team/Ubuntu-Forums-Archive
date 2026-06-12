---
title: "Mplayer/Xine can't play DVD on second DVD drive"
date: 2006-02-06
forum: Desktop Environments
---

### Post by Navyblue on 2006-02-06
Hello,

I have 2 DVD drive on my PC, hdc and hdd.

With Mplayer and Xine, I am able to play DVD on hdc, but not on the hdd.

"mplayer /dev/hdd" gives me this:

```
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /dev/hdd.
Cache fill: 12.50% (131072 bytes)    XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)
XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: Closing plugin /usr/lib/xmms/Input/libtonegen.so
XMMS: Closing plugin /usr/lib/xmms/Input/libcdaudio.so
XMMS: Closing plugin /usr/lib/xmms/Input/libwav.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123.so
XMMS: Closing plugin /usr/lib/xmms/Input/libvorbis.so


Exiting... (End of file)
```

I'd really appreciate if someone could shed some light.

Thank you for reading.

---

### Post by Navyblue on 2006-02-06
After posting this I suddenly had an inspiration and found out that the DMA for my hdd is not turned on (which I thought otherwise). Turning it on solves the problem.

---

