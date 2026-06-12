---
title: "KDE apps don't play ogg files"
date: 2005-07-09
forum: Desktop Environments
---

### Post by justme11 on 2005-07-09
Hi,

I have a problem: When trying to play an ogg file in xmms, it works just fine. However, all KDE apps (kaboodle, juk, noatun, amarok, ...) refuse to play my ogg files. As this seems to be related only to KDE apps, I suspect there is something wrong with kfile's ogg component. Sadly, reinstalling kdemultimedia-kfile-plugins (currently installed in 3.4.0-0ubuntu3) did not resolve the issue. 
Does anyone out there know how to make my ogg files play under KDE apps again?

Thanks in advance!

---

### Post by pipodnmy on 2005-07-09
i suspect that xmms uses its own xmms-ogg-dec lib of some sort that you have installed but you are missing a general ogg decoder..
check if you have these:
libogg0
liboggflac1
liboggflac++
libvorbisfile3

in general run synaptic and search for ogg and vorbis and see what you are missing..

---

### Post by justme11 on 2005-07-10
pipodnmy, I was missing liboggflac++. Installing this und reinstalling all kdemultimedia components solved my problem. Thanks!

EDIT: Well, it was solved at least partly: playing an ogg file worked for about 20 seconds in kaboodle until it crashed. Now it doesn't work any longer at all - same symptoms as before.

---

### Post by justme11 on 2005-07-23
*push*

I can't believe I am the only one having these problems?

---

### Post by tjansson on 2007-04-17
I have somewhat the same problem - with no ogg working in noatun. It works fine in juk though.

---

