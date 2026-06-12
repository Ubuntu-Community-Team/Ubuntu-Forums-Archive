---
title: "dvd backup won't play"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Delp on 2005-12-31
Hi:
I've ripped a dvd with dvdshrink, then i burned the audio_ts and video_ts folders into a blank dvd, but this dvd won't play.  Xine tells me:

```
There is not input plugin avaliable to handle 'dvd:/'.
Maybe MRL syntax is wrong or file/stream source doesn't exit. 
```

and totem:

```
Totem could not play 'dvd:/'.
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
```

So i don't know why (i can play the original dvd's),  i have read many posts, but i haven't found anybody with my problem.

I also have tried dvdbackup, but i doesn't work since it cannot finish the backup itslef.

Thanks a lot.

---

### Post by fabs0028 on 2005-12-31
Well i had the same problem so here is the solution that worked for me :
You probably use totem-xine which needs an additionnal library so in a console type that :

```

sudo apt-get install libdvdplay0

```

OR install it using synaptic.

You need to enable the universe and multiverse repository to install it.

It shoud resolve your problem



Edit :

It seems that you also need libdvdcss2
Take a look at this page for it :
[ubuntu wiki about dvd playing]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28format%29#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b")

---

### Post by Delp on 2005-12-31
Hi, i did both of things, but i have the same problem, nothing has changed...:( 

the error message in xine is:

[CODE]delp@ubuntu:~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[CODE]

Thanks for answering.

---

### Post by lrmall01 on 2005-12-31
If your using DVD shrink try making an ISO image to burn, rather than the VIDEO_TS and AUDIO_TS folders.  DVD players need the files arranged in a certain order on the disk and using the ISO file takes care of this for you.  You should be able to make an ISO and then open it up in Gnomebaker.

Here's a link that I found usefull.
[http://dvd.chevelless230.com/](http://dvd.chevelless230.com/)

---

### Post by bif3c on 2006-03-18
I'm having the exact same problem that Delp first described when he opened this thread.  I first create an iso image (both dvdshrink and k9copy work great for me) that plays perfectly with VLC, but after I burn it to DVD-RW, Totem tells me it seems to be encrypted.  Installing libdvdplay0 did nothing.  GnomeBAker, K3b and NeroLINUX all give the exact same crappy result  If anyone has any ideas, I would really appreciate, because I can't find anything to fix it.

---

