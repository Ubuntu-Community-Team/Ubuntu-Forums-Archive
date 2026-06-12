---
title: "video conversion to quicktime format"
date: 2006-09-07
forum: Desktop Environments
---

### Post by teepark on 2006-09-07
I work for a multimedia company where most people are on Macs. People in this office use After Effects, Quicktime Pro, Final Cut Pro and HD, and even iMovie sometimes. As such, I frequently need to convert DVDs and other MPEGs to quicktime format, and not just MPEGs in a MOV wrapper. I have downloaded Cinelerra, ffmpeg and mencoder, but I can't figure out Cinelerra to save my life (and there's no documentation that came with it or even a 'help' menu), and my attempts with ffmpeg and mencoder from the command line have failed so far.

The most promising command line edits failed with the following errors:
```
$ mencoder movie.vob -ovc qtvideo -o movie.mov -nosound
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Irwindale (Family: 15, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs

WARNING: OUTPUT FILE FORMAT IS _AVI_. see -of help.
success: format: 0  data: 0x0 - 0x40000000
MPEG-PS file format detected.
VIDEO:  MPEG2  352x576  (aspect 2)  25.000 fps  9578.8 kbps (1197.4 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:352x576  fps:25.00  ftime:=0.0400
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!

### Searching for QuickTime plugins (*.qtx) at /usr/lib/win32...
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: AvidQTAVUICodec.qtx
### FindNext: QuickTimeInternetExtras.qtx
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
VDec: vo config request - 352 x 576 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.

SwScaler: BICUBIC scaler, from Planar YV12 to Packed YUY2 using MMX2
Cannot find requested component
FATAL: Cannot initialize video driver.

Exiting...
$

```
```
$ ffmpeg -i movie.vob movie.mov
FFmpeg version CVS, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-a52 --enable-theora --enable-libgsm --enable-x264 --enable-a52bin
  libavutil version: 49.0.0
  libavcodec version: 51.9.0
  libavformat version: 50.4.0
  built on Jun  4 2006 15:08:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, mpeg, from 'movie.vob':
  Duration: 00:00:14.2, start: 0.231578, bitrate: 601370 kb/s
  Stream #0.0[0x1e0], 25.00 fps(r): Video: mpeg2video, yuv420p, 352x576, 9578 kb/s
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 256 kb/s
Output #0, mov, to 'movie.mov':
  Stream #0.0, 25.00 fps(c): Video: mpeg4, yuv420p, 352x576, q=2-31, 200 kb/s
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7ec11a8]removing common factors from framerate
[ac3 @ 0xb7ec11a8]A52 library liba52.so could not be opened!
liba52.so: cannot open shared object file: No such file or directory
Error while opening codec for input stream #0.1
$

```

I can do this kind of transcoding on Mac OS X with ffmpegX, but I'd like to be able to do it in linux from the command line.

I've seen tutorials on command-line ffmpeg and mencoder (that's how I got as far as I have), but they are always concerned with transcoding FROM quicktime format, never the other way around.

---

### Post by zugvogel on 2006-09-09
This is a problem I am also having, and I can't find out how to solve it. In order to edit them in Cinelerra I need to convert from mpeg or dv, to quicktime, but it seems impossible. Does anyone know how to do this?

Incidently, a tutorial for Cinelerra can be found at [http://www.robfisher.net/video/cinelerra1.html](http://www.robfisher.net/video/cinelerra1.html) .

---

### Post by cwaldbieser on 2006-09-09
You need to install:
Package: liba52-0.7.4-dev (0.7.4-1) [universe]

I found this by going to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and searching for the file.

---

