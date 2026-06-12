---
title: "Help with Wii flv conversion"
date: 2009-01-11
forum: General Help
---

### Post by Voorhees1979 on 2009-01-11
Hey all

I am using MCX to stream movies to my kids Wii. The problem I am having is the conversion from avi to flv.

The cmd i am using is:

ffmpeg -i infile.avi -y -b 800 -r 25 -f flv -vcodec flv -ab 128 -ar 44100 outfile.flv

The actual video is pretty blocky so I need to play with the bitrate but the problem I have is the flv has no sound. If I play the flv on totem there is no sound. Same with mplayer. The Wii plays the video but also has no sound.

Any ideas what I am doing wrong to not get any sound?

```
voorhees@voorhees:~$ ffmpeg -i /media/disk/media/movies/Kids/Bee.Movie.avi -y -b 800 -r 25 -f flv -vcodec flv -ab 128 -ar 44100 /media/disk/outfile.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Sep 26 2008 12:56:27, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu1)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from '/media/disk/media/movies/Kids/Bee.Movie.avi':
  Duration: 01:30:40.6, start: 0.000000, bitrate: 1078 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 576x320, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Output #0, flv, to '/media/disk/outfile.flv':
  Stream #0.0: Video: flv, yuv420p, 576x320, q=2-31, 0 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=136015 q=31.0 Lsize=  190002kB time=5440.6 bitrate= 286.1kbits/s    
video:180248kB audio:0kB global headers:0kB muxing overhead 5.411602%
voorhees@voorhees:~$ 


```

Many Thanks for any help

EDIT

No matter what I do I cant get sound from the .flv

---

### Post by FakeOutdoorsman on 2009-01-11
Try adding a "k" after the bitrate:
```
ffmpeg -i infile.avi -y -b 800k -r 25 -f flv -vcodec flv -ab 128k -ar 44100 outfile.flv
```
Otherwise you'll be attempting to encode at a very low bitrate.

---

### Post by Voorhees1979 on 2009-01-14
The k made the video look better thanks. Regards to the sound I had to remove ffmpeg and configure it with the lame codec which now produces sound with the converted flv's :)

For some reason I cannot mark thread as solved. The option isnt under thread tools.

---

### Post by FakeOutdoorsman on 2009-01-14
For others reading this thread: if you don't want to compile your own ffmpeg you can install the **libavcodec-unstripped-51** package which will enable mp3 encoding in ffmpeg.  If you want to compile I wrote a guide on doing just that:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

Mark as Solved has been temporarily (hopefully) removed from the forums while the site admin is monitoring the database.

---

