---
title: "How to make: theora + vorbis = ogg movie"
date: 2006-05-20
forum: Desktop Environments
---

### Post by mich_r on 2006-05-20
Hi

I have an theora movie "Rowerek.ogg" and vorbis sound file "sound.ogg". I thought it is easy to mix them into one ogg file but after several hours spent on it I give up. Can you provide me a tip please.... and don't send me to the manual please, I've been here many times with no success.
Here's the try that looks correct for me (using ffmpeg) , but unfortunatelly the produced file is unplayable (below the mplayer output) :(
```
mich_r@ubuntu:~$ ffmpeg -i Filmy/Bajki/Rowerek.ogg -vcodec copy -i sound.ogg -acodec copy -f ogg movie.ogg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, ogg, from 'Filmy/Bajki/Rowerek.ogg':
  Duration: 00:10:17.4, start: 0.000000, bitrate: 513 kb/s
  Stream #0.0: Video: theora, yuv420p, 320x240, 25.00 fps
Input #1, ogg, from 'sound.ogg':
  Duration: 00:10:18.3, start: 0.000000, bitrate: 64 kb/s
  Stream #1.0: Audio: vorbis, 44100 Hz, mono, 64 kb/s
File 'movie.ogg' already exists. Overwrite ? [y/N] y
Output #0, ogg, to 'movie.ogg':
  Stream #0.0: Video: 0x0000, 320x240, 25.00 fps, q=2-31
  Stream #0.1: Audio: vorbis, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
error, non monotone timestamps 18286168 >= 18284263
error, non monotone timestamps 192056303 >= 192053696 563.4kbits/s
error, non monotone timestamps 241825209 >= 241811156 571.9kbits/s
frame=15437 q=0.0 Lsize=   43628kB time=617.5 bitrate= 578.8kbits/s
video:38323kB audio:4838kB global headers:0kB muxing overhead 1.080870%

```



```
mich_r@ubuntu:~$ gmplayer movie.ogg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE




vo: X11 running at 1280x1024 with depth 16 and 16 bpp (":0.0" => local display)
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
Playing /home/raatz/movie.ogg.
SUB: error opening iconv descriptor.
SUB: error opening iconv descriptor.
Ogg stream 0 is of an unknown type
SUB: error opening iconv descriptor.
**Ogg stream 0 is of an unknown type**
XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libmikmod.so (MikMod Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)
XMMS: found plugin: libmpg123-ja.so (MPEG Layer 1/2/3 Player 1.2.10j_20040302)
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123-ja.so
XMMS: Closing plugin /usr/lib/xmms/Input/libvorbis.so
XMMS: Closing plugin /usr/lib/xmms/Input/libtonegen.so
XMMS: Closing plugin /usr/lib/xmms/Input/libcdaudio.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmikmod.so
XMMS: Closing plugin /usr/lib/xmms/Input/libwav.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123.so


Exiting... (Quit)

```

---

