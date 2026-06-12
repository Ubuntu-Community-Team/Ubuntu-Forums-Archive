---
title: "Anime / video Fansubbing tools in linux?"
date: 2005-12-08
forum: General Help
---

### Post by 0okami on 2005-12-08
Any anime fansubbers in here who can help me? 

Im trying to find a good tool for editing/adding translated scripts (subtitles)  anime. 

In windows I used VisualSubsync, Substation alpha, Sabbu, VirtualDub, VobSub and a few other programs... 

However, the only one i have come across is sabbu (for linux) and I cant seem to compile that one to check it out (im still new to linux)

---

### Post by pizzach on 2005-12-08
Ooo.  Subbu looks like a nice program.  What is your compiling problem?  

Looking at the requirements on [http://www.sabbu.com/en/index.html](http://www.sabbu.com/en/index.html) a good place to start is by sudo apt-get-ing:

sudo apt-get libsndfile1 libsndfile1-dev ffmpeg

Hm...don't know if you need the dev files for ffmpeg.  But that depends on what your error(s) are.  I don't see ffmpeg-dev in Synaptic so the second choice would be to compile ffmpeg and install.
[B]
Go to and download ffmpeg[/B]
[http://sourceforge.net/projects/ffmpeg/](http://sourceforge.net/projects/ffmpeg/)

In the terminal...

**untar it**
tar -xvvzf filename.tar.gz  
**enter folder**
cd foldername
**general install procedure...**
./configure --prefix=/usr
make
sudo make install

:D  I think I covered everything

---

### Post by 0okami on 2005-12-08
Thanks! I will get right on to this as soon as i shake off this migrain :(

---

### Post by applechewer_ on 2006-04-10
Hi

I am in the same situation as 0okami was, where sabbu won't compile. I managed to sort out the problems with GTK2 and libsndfile versions, but it still tells me

"configure: error: ffmpeg >= 0.4.9-pre1 is required for video features. You may specify --without-ffmpeg to disable video features."

even though apt-get insists that I have the newest version. I assumed that if I download and compile ffmpeg it may well fix this, but the link pizzach provided (and the link on the ffmpeg website) doesn't lead anywhere. ](*,) Anyone know anywhere else to download it from?

Thanks everyone!

---

### Post by pizzach on 2006-04-10
[QUOTE=applechewer_]Hi

I am in the same situation as 0okami was, where sabbu won't compile. I managed to sort out the problems with GTK2 and libsndfile versions, but it still tells me

"configure: error: ffmpeg >= 0.4.9-pre1 is required for video features. You may specify --without-ffmpeg to disable video features."

even though apt-get insists that I have the newest version. I assumed that if I download and compile ffmpeg it may well fix this, but the link pizzach provided (and the link on the ffmpeg website) doesn't lead anywhere. ](*,) Anyone know anywhere else to download it from?

Thanks everyone![/QUOTE]

```
sudo apt-get install cvs
```

then use cvs to get it from:

```
cvs -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg login
cvs -z3 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co -P ffmpeg
```

as described on the Mplayer webpage 
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Hope that helps.  ffmpeg is floating around the web somewhere.  Last time I installed it was this way though.

---

### Post by applechewer_ on 2006-04-10
Thanks for your help pizzach, but it still does the same thing. After installing ffmpeg from the CVS, 'ffmpeg -version' now returns
```
FFmpeg version CVS, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:
  libavutil version: 49.0.0
  libavcodec version: 51.9.0
  libavformat version: 50.4.0
  built on Apr 10 2006 18:54:57, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
ffmpeg      CVS
libavutil   3211264
libavcodec  3344640
libavformat 3277824
```
but sabbu's configure still tells me
```
error: ffmpeg >= 0.4.9-pre1 is required for video features
```
I thought perhaps this is because the version shows up as 'CVS', and configure may be expecting a number. Any more thoughts?

Thanks again!

---

### Post by pizzach on 2006-04-10
I'm going to try to compile it so I can give you exact directions.

---

### Post by 0okami on 2006-05-04
any news on this?

---

