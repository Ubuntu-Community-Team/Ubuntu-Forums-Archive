---
title: "WinFF/ffmpeg - Ubuntu 12.04 - Xvid Fullscreen"
date: 2012-05-23
forum: Desktop Environments
---

### Post by barthus on 2012-05-23
Dear all.

I recently installed Ubuntu 12.04 (64 Bit) from scratch. Now I have an issue with WinFF/ffmpeg, which didn't appear under Ubuntu 10.10. 

I have a raw data movie (640x480) from a digital camera and want to compress it via WinFF: AVI, XviD FullScreen - What I get is an error message:

```

ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
Input #0, avi, from '/media/usr/MVI_9568.AVI':
  Metadata:
    creation_time   : 2012-05-16 14:38:12
    encoder         : CanonMVI02
  Duration: 00:00:20.06, start: 0.000000, bitrate: 15054 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: pcm_u8, 11024 Hz, 1 channels, u8, 88 kb/s
Incompatible pixel format 'yuvj422p' for codec 'libxvid', auto-selecting format 'yuv420p'
[buffer @ 0x1967d00] w:640 h:480 pixfmt:yuvj422p
[scale @ 0x1965a20] w:640 h:480 fmt:yuvj422p -> w:640 h:480 fmt:yuv420p flags:0x4
Incompatible sample format 'u8' for codec 'libmp3lame', auto-selecting format 's16'
[libxvid @ 0x1963300] [Eval @ 0x7fffec16e9e0] Undefined constant or missing '(' in 'aic'
[libxvid @ 0x1963300] Unable to parse option value "aic"
[libxvid @ 0x1963300] Error setting option trellis to value -aic.
Output #0, avi, to '/home/usr/o_MVI_9568.avi':
    Stream #0.0: Video: mpeg4 (hq), yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=3-5, 1500 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, 2 channels, s16, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```As written above, all worked well under 10.10.

Any suggestions? Thanks in advance.

---

### Post by barthus on 2012-05-23
Solved! :guitar:

have a look here and follow Paul Gevers advice:

[http://groups.google.com/group/winff/browse_thread/thread/9a3907b693a6b5b8?fwc=1](http://groups.google.com/group/winff/browse_thread/thread/9a3907b693a6b5b8?fwc=1)

Thanks a lot for reading, cheers.

---

### Post by washy75 on 2012-05-23
Hi there my friend, I've managed to fix this by following this few steps.

1 - Download WinFF from Launchpad web site: [http://launchpadlibrarian.net/90434679/winff_1.4.1-1_amd64.deb]("http://launchpadlibrarian.net/90434679/winff_1.4.1-1_amd64.deb")

2 - I installed libavcodec-extra-53
# aptitude install libavcodec-extra-53

3 - Then I edited WinFF presets and changed it by simply getting rid of -trellis -aic

# nano -c ~/.winff/presets.xml

BEFORE
<XviDAVIWS>
    <label>XviD Widescreen</label>
$ -bufsize 4096 -mbd 2 -bf 2 **-trellis -aic** -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2</params>
    <extension>avi</extension>
    <category>AVI</category>

AFTER
<XviDAVIWS>
    <label>XviD Widescreen</label>
$ -bufsize 4096 -mbd 2 -bf 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2</params>
    <extension>avi</extension>
    <category>AVI</category>

4 - Do it in every preset you want to use. This -trellis -aic is no longer used or required.

Hope I have helped. God bless you.

---

### Post by barthus on 2012-05-23
> **washy75 said:**
> Hope I have helped. God bless you.

Thanks a lot. I solved it as described above ... probably the same what you propose. 

Wouldn't it be better if all this comes already 'in perfect shape' when installed via sudo apt-get under Ubuntu?

---

### Post by pabloikba on 2012-06-02
I've followed the instructions and get this error (scroll down to bottom) and can't figure out how to make WinFF work under Ubuntu 12.04:

ffmpeg version 0.10.2-4:0.10.2-0ubuntu0jon1 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar 18 2012 09:59:38 with gcc 4.6.3
  configuration: --extra-version='4:0.10.2-0ubuntu0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-gpl --enable-postproc --enable-x11grab --enable-librtmp --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avutil      configuration: --extra-version='4:0.10.2.0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-libopenjpeg --enable-gpl --enable-postproc --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --extra-version='4:0.10.2.0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-libopenjpeg --enable-gpl --enable-postproc --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/pablo/Desktop/052912 chelsea.lately.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2012-05-30 10:36:55
  Duration: 00:22:08.96, start: 0.000000, bitrate: 1023 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 720x404, 899 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Metadata:
      creation_time   : 2012-05-30 10:25:36
      handler_name    : GPAC ISO Video Handler
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, s16, 119 kb/s
    Metadata:
      creation_time   : 2012-05-30 10:36:55
      handler_name    : GPAC ISO Audio Handler
Please use -b:a or -b:v, -b is ambiguous
Unknown encoder 'libxvid'
Press Enter to Continue

Any suggestions?

Thanks, all help will be appreciated.

P

---

### Post by FakeOutdoorsman on 2012-06-04
> **pabloikba said:**
> ```
Unknown encoder 'libxvid'
```

You probably need to install the **libavcodec-extra-53** package. More info: [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

---

### Post by pabloikba on 2012-06-04
Thanks for your reply.

I will try the solution(s) suggested and report back.

---

### Post by pabloikba on 2012-06-04
I've done what you suggested...now I am getting this:

ffmpeg version 0.10.2-4:0.10.2-0ubuntu0jon1 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar 18 2012 09:59:38 with gcc 4.6.3
  configuration: --extra-version='4:0.10.2-0ubuntu0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-gpl --enable-postproc --enable-x11grab --enable-librtmp --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avutil      configuration: --extra-version='4:0.10.2.0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-libopenjpeg --enable-gpl --enable-postproc --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --extra-version='4:0.10.2.0jon1' --arch=amd64 --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-vaapi --enable-frei0r --enable-libopenjpeg --enable-gpl --enable-postproc --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/pablo/Desktop/052912 chelsea.lately.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2012-05-30 10:36:55
  Duration: 00:22:08.96, start: 0.000000, bitrate: 1023 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 720x404, 899 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Metadata:
      creation_time   : 2012-05-30 10:25:36
      handler_name    : GPAC ISO Video Handler
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, s16, 119 kb/s
    Metadata:
      creation_time   : 2012-05-30 10:36:55
      handler_name    : GPAC ISO Audio Handler
Please use -b:a or -b:v, -b is ambiguous
Unknown encoder 'libxvid'
Press Enter to Continue

This is the preset for xvid widescreen as copied from Winff: 
-f avi -r 29.97 -vcodec libxvid -vtag XVID -vf scale=704:384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis 1 -flags +aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2

It seems pretty much the same as before....any more suggestions, please?

Thanks

---

### Post by pabloikba on 2012-06-04
A little tweaking and am getting closer but I am still needing some help. I changed the preset to read:

-f avi -r 29.97 -vcodec mpeg4 -vtag XVID -vf scale=704:384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis 1 -flags +aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2

Now, the only error I am getting is:

Please use -b:a or -b:v, -b is ambiguous

I have tried to change "-b" that is after "1800k" to "-b:v" and to "-b:a".....after doing that, I get the same error.

What is it I need to change?

Thanks

---

