---
title: "ffmpeg problem"
date: 2010-06-22
forum: Desktop Environments
---

### Post by andrea000 on 2010-06-22
What is going on with svn ffmpeg libfaad doesn't install
and i can't rip a youtube to a mp3?I guess i will need to
go back to 0.5.

---

### Post by andrew.46 on 2010-06-23
Hi andrea,

Times have changed and faad is no longer required to decode AAC:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs help | grep -i 'aac'[/COLOR]**
FFmpeg version SVN-r23727, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 23 2010 09:19:56 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static
 --disable-ffserver --enable-libtheora --enable-libvorbis 
--enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 
--enable-zlib --enable-libvpx --enable-nonfree --enable-gpl
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"] DEA    aac             Advanced Audio Coding[/COLOR]**
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```

So you can see that FFmpeg now has a *native* encoder decoder. Can you post the command and full terminal output for the command that failed for you?

Andrew

---

### Post by andrea000 on 2010-06-23
Thank you

I also took --enable-libfaad out and installed it but it still would
not work.I installed the ffmpeg 0.5 to do the ripping but i will
install the newest tomorrow night and post the output

---

