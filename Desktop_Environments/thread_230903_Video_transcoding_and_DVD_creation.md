---
title: "Video transcoding and DVD creation ???"
date: 2006-08-06
forum: Desktop Environments
---

### Post by mips on 2006-08-06
Yes I did a search and found some stuff but hoping for more help.

I have two video files I would like to write to DVD in order to play on my dvd player/tv.

**File1.avi****-**
Type: Microsoft AVI Video
Size: 666.4MB
Meta Info:
Length 1:22:37
Resolution 640x480
Frame Rate 25fps
Video Codec div4x
Audio Codec mp3

**File2**.**mpg**-
Type: MPEG Video
Contents: Microsoft AVI Video
Size: 626.2MB
Meta Info: NONE

**For File1 I tried:**
mips@obelix:~/downloads$ ffmpeg -i File1.avi -target pal-dvd /home/mips/File1.mpg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Délires: I/O error occured
Usually that means that input file is truncated and/or corrupted.

**For File2:**
Don't even know where to start as it says it is a avi inside an mpg ?

Can someone please help me with this or point me in the right direction ?

---

### Post by orb9220 on 2006-08-06
Ok First of all check your dvd player. Most players can play a range of mpegs,avi's,divx's type files. all you have to do is burn them to a dvd or cd.

My player is like 4 years old and it plays mpeg-1 but not avi's or divx

Hope this helped.

---

### Post by mips on 2006-08-08
I have a NAD T531 and as far as I know it only does MPEG so I have to create a standard DVD as per one you would purchase in a shop.
[http://207.228.230.231/info/NAD_T531.pdf](http://207.228.230.231/info/NAD_T531.pdf)

---

### Post by mips on 2006-08-09
bump

---

### Post by mips on 2006-08-10
Looks like I'll have to boot into windows to do this then, arrggghhh

---

