---
title: "Every media player freezes when trying to play this DVD"
date: 2009-04-09
forum: General Help
---

### Post by crazyfuturamanoob on 2009-04-09
Yeah. So far I tried Kaffeine, Totem, and MPlayer. All just freeze when trying to play the DVD.

Worked great in the past. Maybe the disk is scratched? Why?

Edit: Works with VLC. I need separate media players for every task. :/

---

### Post by askreet on 2009-04-09
Futurama is awesome, but that's not why I'm here.

Try running a failing media player from a terminal and see what output you get.
$ mplayer dvd://

Also, while you're having errors what do you see?  Disk re-reading a lot?  Application crashes/hangs?

Check the output of `dmesg` right after you're having issues.
$ sudo dmesg|tail

HTH,
askreet

---

### Post by askreet on 2009-04-09
I was just reminded of something:
All of the media players you listed are using gstreamer, except VLC.  VLC has internal codecs, etc. 

Have you installed DVD support?
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20%28i386,%20amd64%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20%28i386,%20amd64%29)

---

### Post by crazyfuturamanoob on 2009-04-09
I have watched many DVD's in the past, so I probably got DVD stuff installed. 

Anyways I just watched the movie with VLC. I wish I had only one movie player to use for everything.

---

### Post by askreet on 2009-04-09
> **crazyfuturamanoob said:**
> I have watched many DVD's in the past, so I probably got DVD stuff installed. 

Anyways I just watched the movie with VLC. I wish I had only one movie player to use for everything.

You do, VLC.  =)

---

