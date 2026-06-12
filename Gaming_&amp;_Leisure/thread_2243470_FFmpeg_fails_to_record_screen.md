---
title: "FFmpeg fails to record screen"
date: 2014-09-09
forum: Gaming &amp; Leisure
---

### Post by thekiwi5000 on 2014-09-09
Hello,
I recently found a script that records screen, using x11grab and ffmpeg
```
avconv version 0.8.13-6:0.8.13-0ubuntu0.13.10.1, Copyright (c) 2000-2014 the Libav developers
  built on Jul 15 2014 13:53:49 with gcc 4.8.1
[x11grab @ 0x9c10800] device: :0.0+66,52 -> display: :0.0 x: 66 y: 52 width: 1667 height: 1010
[x11grab @ 0x9c10800] shared memory extension  found
[x11grab @ 0x9c10800] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0+66,52':
  Duration: N/A, start: 1410246870.159256, bitrate: 1293058 kb/s
    Stream #0.0: Video: rawvideo, bgra, 1667x1010, 1293058 kb/s, 24 tbr, 1000k tbn, 24 tbc
[alsa @ 0x9c1dca0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9c1dca0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1410246869.998155, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
File 'out.flv' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'flv', auto-selecting format 'yuv420p'
[buffer @ 0x9bea280] w:1667 h:1010 pixfmt:bgra
[scale @ 0x9c23fe0] w:1667 h:1010 fmt:bgra -> w:854 h:480 fmt:yuv420p flags:0x4
Output #0, flv, to 'out.flv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: flv, yuv420p, 854x480, q=2-31, 200 kb/s, 1k tbn, 24 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> flv)
  Stream #1:0 -> #0:1 (pcm_s16le -> pcm_s16le)
Press ctrl-c to stop encoding
Audio encoding failed


```
and here's code i use:
```
avconv -f x11grab -s $INRES -r "$FPS" -i :0.0+$TOPXY  -f alsa -i pulse -vcodec flv -s $OUTRES  -acodec pcm_s16le -ar 44100  -threads $THREADS  -bufsize 1024k -force_key_frames 2 -f flv out.flv
```

---

### Post by FakeOutdoorsman on 2014-09-10
But you're using avconv.

---

### Post by sffvba[e0rt on 2014-09-12
From the output it seems video was encoded and not audio.  Did it fail completely or did you press Ctrl + C?  

There is a [PPA]("https://launchpad.net/~jon-severinsson/+archive/ubuntu/ffmpeg") for ffmpeg (as it isn't in Ubuntu 14.04) and also various applications that work to capture your screens... [SimpleScreenRecorder]("http://www.maartenbaert.be/simplescreenrecorder/") being one I recommend :)

---

### Post by dannyboy79 on 2014-09-15
2 other great pieces of software for recording AND livestreaming to twitch or hitbox are
-screenstudio
-obs-studio

---

