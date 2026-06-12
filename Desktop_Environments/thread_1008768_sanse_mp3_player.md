---
title: "sanse mp3 player"
date: 2008-12-11
forum: Desktop Environments
---

### Post by mitchroberts on 2008-12-11
I have a sansa connect mp3 player and looking to convert avi files to mp4
does anyone know a program for Ubuntu to  do this?

---

### Post by Denestria on 2008-12-11
To do this for my iRiver Lplayer I installed ffmpeg, winff and the "unstripped" libraries, not sure all these are really needed but I installed them anyway.
```

libavcodec-unstripped-51
libavdevice-unstripped-52
libavformat-unstripped-52
libavutil-unstripped-49
libpostproc-unstripped-51
libswscale-unstripped-0

```
Opened winff and added a new preset with these options (mpeg4-sp) which might be a little different for your Sansa.
```

-vcodec mpeg4 -vtag XVID -profile 0 -b 384k -s 320x240 -r 30 -acodec libmp3lame -ab 128k -ar 44100 -ac 2 -f avi

```
then I just 'add' the file and select the type and preset from the dropdown and 'convert'.

---

### Post by girishsasikumar on 2008-12-12
The best and easiest converter I found was WINFF, maybe you should try it out from this website
[http://code.google.com/p/winff/]("http://code.google.com/p/winff/")

---

