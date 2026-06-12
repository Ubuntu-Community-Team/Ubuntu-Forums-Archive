---
title: "Making DVDs from .mp4 files"
date: 2006-03-23
forum: Desktop Environments
---

### Post by OneSeventeen on 2006-03-23
I've got some .mp4 files from my church and I want to burn them to DVD for a road trip tomorrow, but I can't seem to transcode the video and audio.

When streaming to a file using VLC, the audio comes over just fine, but the video doesn't (ffmpeg cannot decode one frame is repeated a few thousand times).

When using ffmpeg from the command line, I get this:
```

oneseventeen@tigershark:~/000temp$ ffmpeg -i 20060319.mp4 -target ntsc-dvd calvarytest.mpg ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)

Seems that stream 1 comes from film source: 2997.00 (2997/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2, from '20060319.mp4':
  Duration: 00:50:03.9, start: 0.000000, bitrate: 366 kb/s
  Stream #0.0: Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1: Video: h264, yuv420p, 320x240, 2997.00 fps
Output #0, dvd, to 'calvarytest.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, q=2-31, 6000 kb/s  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 448 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec (id=86018) for input stream #0.0

```

Any ideas why this wouldn't work?

You can download a sample video in the format I'm working with [here](http://video.calvaryabq.org/videopodcasts/20060319.mp4). (117MB, ha!)

I'd really like to get this done tonight, so if I find anything while I'm trying it, I'll post here.  Oh, and trying to make ffmpeg from source just gave me errors:
```

oneseventeen@tigershark:~/downloads/open_source/ffmpeg-0.4.9-pre1$ make
make -C libavcodec all
make[1]: Entering directory `/home/oneseventeen/downloads/open_source/ffmpeg-0.4.9-pre1/libavcodec'
gcc -O3 -g -Wall  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -o common.o common.c
In file included from avcodec.h:14,
                 from common.c:28:
common.h:67: error: array type has incomplete element type
common.h:71: error: array type has incomplete element type
make[1]: *** [common.o] Error 1
make[1]: Leaving directory `/home/oneseventeen/downloads/open_source/ffmpeg-0.4.9-pre1/libavcodec'
make: *** [lib] Error 2

```

I'm more concerned about getting the .mp4 file to something I can burn to DVD to play on a set-top player than getting ffmpeg to work.

**EDIT:** I can play the video file in VLC just fine, but cannot play it in totem for some reason.

---

