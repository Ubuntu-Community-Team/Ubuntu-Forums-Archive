---
title: "Recording Screen with ffmpeg - error"
date: 2020-05-27
forum: Desktop Environments
---

### Post by robertcull1 on 2020-05-27
Trying to record screen with ffmpeg. Can't seem to figure it out.

```
$ ffmpeg -y -f alsa -i hw:0 -f x11grab -framerate 30 -video_size 1600x900 -i :0.0+0,0 -c:v libx264 -pix_fmt yuv420p -qp 0 -preset ultrafast moetoVideo.avi


ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, alsa, from 'hw:0':
  Duration: N/A, start: 1590607126.762333, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Invalid MIT-MAGIC-COOKIE-1 key[x11grab @ 0x55e9cfa6aa20] Cannot open display :0.0+0,0, error 1.
:0.0+0,0: Input/output error

```

Please help if you can.

---

### Post by ajgreeny on 2020-05-27
I can not get your command to work either, mine giving a final error
```
[alsa @ 0x560bc4350980] cannot open audio device hw:0 (No such file or directory)
hw:0: Input/output error
```
Unfortunately my code skills are not good enough to figure out what is wrong with your command.

I do, however, have two commannds which both work fine; the first has no sound recorded, the second does have sound, though I have not been able to test that at the moment.  Try these and see if they are any use to you
```
ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -qscale 0 Desktop/video.avi
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec flac -vcodec libx264 -threads 0 ./Desktop/mydesktop.mkv
```
You will probably need to amend the resolution figures in these to suit your own case, so I wll have to leave that to you to figure out.
Note also that the first command records the whole desktop @1440x900, but then reduces the output to half that, ie, 720x450.

Good luck; I hope this is useful.

---

### Post by robertcull1 on 2020-05-27
Thanks!

Tried the second one with sound and I got the following error:

```
$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec flac -vcodec libx264 -threads 0 ./Desktop/mydesktop.mkv
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1590614069.562419, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Invalid MIT-MAGIC-COOKIE-1 key[x11grab @ 0x5564635ad780] $ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec flac -vcodec libx264 -threads 0 ./Desktop/mydesktop.mkv
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1590614069.562419, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Invalid MIT-MAGIC-COOKIE-1 key[x11grab @ 0x5564635ad780] Cannot open display :0.0, error 1.
:0.0: Input/output error
:0.0: Input/output error

```

---

### Post by ajgreeny on 2020-05-28
What about the other command; did that work even if silent?

Can I also check whether you are using an **xorg** or a **wayland** session, as I suspect those commands will not work if using wayland because there will be no x11 to grab, though I have almost no knowledge of wayland so far so can't be sure.

---

### Post by jp41 on 2020-05-28
if its just a screen recorder you're looking for ,why not try Kazam? it's pretty straight forward

---

### Post by ajgreeny on 2020-05-29
There's also simplescreenrecorder which is now in the repos for 20.04.  It's in the universe repos which I think you may need to enable in software sources if you're using Ubuntu.

---

### Post by mc4man on 2020-05-30
Should be able to use x11grab in wayland, at least is ok in 20.04, don't have wayland available in my 18.04.
Run this to see if  display is :0, if not then  adjust command.
```
echo $DISPLAY
```

---

