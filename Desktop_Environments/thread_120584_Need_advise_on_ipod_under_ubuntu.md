---
title: "Need advise on ipod under ubuntu"
date: 2006-01-22
forum: Desktop Environments
---

### Post by otey on 2006-01-22
I just bought the 60GB ipod, and i was wondering... 

What is the best way to connect and transfer music to my ipod?

I've been trying to use VM player (running WinXP pro SP2). I created a network drive to mount my samba shared ext3 harddisk, containing all my music. It works, but I still have some problems getting my ipod to work with VM player. Something about the usb2 drivers.. i think..

I also tryed using amarok, but it fails somehow, and only transfers half the files it's surposed to. 

Does anybody out there have an iPod, and what do you use to transfer music?

---

### Post by shanghaipi on 2006-01-22
use yamipod or gtkpod....yamipod actually synchronizes your music folder.  I prefer it better than gtkpod.  but gtkpod is a solid choice.

You can get gtkpod via synaptic

you have to get yamipod here: [www.yamipod.com](www.yamipod.com)

---

### Post by hatstand on 2006-01-22
I use gtkpod. it is excellent for music and does album art. People are right now working to make it sync videos. I have not heard how to sync photos.

---

### Post by dombleu on 2006-01-22
I use gtkpod without any issue. 

But.

My ipod is 3rd gen. and yours is 4th if i'm not wrong. So things may not be the same here and by your side.

That given. Did the ipod mount correctly as a hardrive? That should be the first step to overcome. Every issue I got with my ipod have been related to permission/access problems.

If the access is flaky with firewire, give it a try with usb. 

Maybe you could try to put a line in /etc/fstab to explicitely get things working the way you want. But I don't. It's automatically detected and mounted as /media/ipod .

---

### Post by jetpeach on 2006-01-23
I have an ipod video 5th? generation also.  I have had a very difficult time getting it working, but I'm running Ubuntu with KDE installed, then upgraded KDE to 3.5.  There are tons of problems with HAL and needing to upgrade libraries with that.  It doesn't work in Gnome either though now, but I'm not sure if it's because I messed it up while trying to get it to work in KDE...

---

### Post by otey on 2006-01-27
Hi again.. Here's a status message.

I use gtkpod now, and it works perfectly.. though i'm not able to transfer movies yet. I'll have to compile gtkpod with something to be able to do that.. Found a tutorial, but the video thing can wait for later. For now I use samba share to get access to my videofiles from windows xp, using itunes. (not vm player windows xp)

The viatual machine did not work for me.. some problems with usb2 devices i think. 

Anyway.. I have a problem when closing the program (gtkpod). It writes "Unmounting of '/media/ipod' (/dev/sda2) unsuccessful." But the Ipod seems ready for unplugging. No "do not disconnect" sign or anything. How do i get rid of this warning?

---

