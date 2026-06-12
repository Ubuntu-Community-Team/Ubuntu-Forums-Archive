---
title: "Mplayer: error with -vo xv"
date: 2006-06-06
forum: Desktop Environments
---

### Post by miceagol on 2006-06-06
I can't play anything in Mplayer, I doesn't seem to find the xv video filters...:
```

michaeka@laptop:~/filmer$ mplayer Within\ Temptation\ -\ Running\ Up\ That\ Hill.avi
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


Warning unknown option skin at line 52
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing Within Temptation - Running Up That Hill.avi.
Cache fill:  0.00% (0 bytes)    AVI file format detected.
VIDEO:  [DX50]  720x544  24bpp  24.998 fps  3079.3 kbps (375.9 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Requested audio codec family [mad] (afm=libmad) not available.
Enable it at compilation.
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
AF_pre: 44100Hz/2ch/s16le
AO: [oss] 44100Hz 2ch s16le (2 bps)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 544 (preferred csp: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Can't restore text mode: Invalid argument

Exiting... (End of file)

```

...although it is present on my system according to xvinfo:
```

michaeka@laptop:~/filmer$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Mach64 Back-end Overlay Scaler"
    number of ports: 1
    port base: 61
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 12
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 391)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 15)
      "XV_COLOUR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 391)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 391)
      "XV_AUTOPAINT_COLOURKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLOURKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 197121)
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 197121)
      "XV_COLOURKEY_MASK" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 16777215)
      "XV_COLORKEY_MASK" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 16777215)
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 720 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```

No, it doesn't work with -vo x11 either :), and -vo help lists the following filters:
```

michaeka@laptop:~/filer/nedlast/MPlayer-1.0pre7try2$ mplayer -vo help
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
Good morning, Blindern
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


Warning unknown option skin at line 52
Available video output drivers:
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        vesa    VESA VBE 2.0 video output
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```

I'm using Ubuntu 'Breezy Badger' and kernel version 2.6.12-9-386. Mplayer was installed with a package:
```

root@laptop:/usr/lib# apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
Suggested packages:
  w32codecs libdvdcss mplayer-doc
The following packages will be REMOVED:
  mplayer-386
The following NEW packages will be installed:
  liblame0 mplayer-586
0 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 3910kB of archives.
After unpacking 176kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://no.archive.ubuntu.com breezy/multiverse liblame0 3.96.1-1 [151kB]
Get:2 http://no.archive.ubuntu.com breezy/multiverse mplayer-586 1:1.0-pre7cvs20         050716-0.1ubuntu9 [3759kB]
Fetched 3910kB in 31s (124kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "nb_NO:nb:no_NO:no:en_GB:en",
        LC_ALL = (unset),
        LANG = "nb_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
dpkg: mplayer-386: dependency problems, but removing anyway as you request:
 mplayer-fonts depends on mplayer; however:
  Package mplayer is not installed.
  Package mplayer-386 which provides mplayer is to be removed.
(Reading database ... 82236 files and directories currently installed.)
Removing mplayer-386 ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "nb_NO:nb:no_NO:no:en_GB:en",
        LC_ALL = (unset),
        LANG = "nb_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Selecting previously deselected package liblame0.
(Reading database ... 82141 files and directories currently installed.)
Unpacking liblame0 (from .../liblame0_3.96.1-1_i386.deb) ...
Selecting previously deselected package mplayer-586.
Unpacking mplayer-586 (from .../mplayer-586_1%3a1.0-pre7cvs20050716-0.1ubuntu9_i386.deb) ...
Setting up liblame0 (3.96.1-1) ...

Setting up mplayer-586 (1.0-pre7cvs20050716-0.1ubuntu9) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "nb_NO:nb:no_NO:no:en_GB:en",
        LC_ALL = (unset),
        LANG = "nb_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

I have no problems playing videos in VLC, and I beleive that it uses the same filter. Does this and the output from xvinfo imply that Mplayer doesn't find the xv filter? Where is the xv filter located, and how do I configure mplayer to find it?

---

### Post by miceagol on 2006-06-17
This issue was solved with a clean install of Dapper Drake. Apparently the package libxv-dev was missing.

---

### Post by precinto on 2006-07-03
I'm having the same problem, but installing libxv-dev and even reinstalling libxv, doesn't work. And I wouldn't like to do a fresh install...

---

