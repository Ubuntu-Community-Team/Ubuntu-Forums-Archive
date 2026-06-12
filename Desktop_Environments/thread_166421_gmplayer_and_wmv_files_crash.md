---
title: "gmplayer and wmv files crash"
date: 2006-04-26
forum: Desktop Environments
---

### Post by tarasbulba on 2006-04-26
Hello.First sorry for my english.I have Dapper Drake flight 6 installed.I've mplayer,gmpalyer and kmplayer installed too via synaptic.I installed mplayer and synaptic installed gmplayer.Good lookink gui with skins.No problem.I've insatalled all codecs,including essential codecs.Here is the problem with gmplayer:crashes with wmv files.Neither mplayer8via conole command) nor kmplayer crashes.But gmplayer crashes.Below outputs of commandline:

For gmplayer:
> tarakbumba@ubuntu:~$ gmplayer Filmler/clip06.wmv
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu6 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



91 audio & 204 video codecs
/usr/share/mplayer/subfont.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/mplayer/subfont.ttf
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
[GUI] Adding video filter: pp
Playing /home/tarakbumba/Filmler/clip06.wmv.
ASF file format detected.
VIDEO:  [WMV3]  352x240  24bpp  1000,000 fps    0,0 kbps ( 0,0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32,0 kbit/4,54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Opening video filter: [pp]
==========================================================================
Trying to force video codec driver family vfwex...
Opening video decoder: [dmo] DMO video codecs
Called unk_RegOpenKeyA
Called unk_RegQueryValueExA
Called unk_RegCloseKey


MPlayer interrupted by signal 11 in module: init_video_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

For mplayer:
> tarakbumba@ubuntu:~$ mplayer Filmler/clip06.wmv
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu6 (C) 2000-2006 MPlayer Team
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
Playing Filmler/clip06.wmv.
ASF file format detected.
VIDEO:  [WMV3]  352x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:253440  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 352 x 240 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 352x240 => 352x240 Planar YV12  [zoom]
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 22050 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Starting playback...
A:  17.9 V:  18.0 A-V: -0.054 ct: -0.114 451/451  4%  0%  0.4% 0 0
alsa-uninit: pcm closed

Exiting... (End of file)

Can anyone help me?I can't understand gmplayer crashes while mplayer doesn't?
I don't want to use kmplayer...

---

