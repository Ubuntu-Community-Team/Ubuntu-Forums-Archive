---
title: "Extracting sound from video files"
date: 2005-11-10
forum: Desktop Environments
---

### Post by kreso on 2005-11-10
Is there such a program for Linux?

---

### Post by Joe_lurker on 2005-11-10
I use mplayer to rip audio from DVD (concerts, Start Trek, etc.) for listening on MyPod.
You would run a command such as: ```
mplayer -vc dummy -vo null -ao pcm:file~/my.wav my.avi
```
This would extract the audio from the file my.avi to the file my.wav in your home folder.

From there you can conver it to an MP3 or whatever using LAME or Sound Converter.

-Joe

---

### Post by RAOF on 2005-11-10
ffmpeg is also a good program, which can do what you want.  It's in the repositories.

You'd run something like
```
ffmpeg -i inputfile outputfile.mp3
```
but it's hugely versatile - it will accept pretty much any multimedia input file and output to pretty much any format.

Particular options you will want are: -vn (to disable video processing), -acodec (to choose the output audio codec), -ab (to choose the output bitrate)

---

