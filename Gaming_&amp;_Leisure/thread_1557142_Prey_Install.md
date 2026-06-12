---
title: "Prey Install"
date: 2010-08-20
forum: Gaming &amp; Leisure
---

### Post by Raffles10 on 2010-08-20
I have Prey on DVD and have been trying to install using the Linux installer from:

[Prey for Linux]("http://icculus.org/prey/")

The problem is with the DVD in the drive the installer keeps asking "Please insert Prey Disc 1". I've tried removing the DVD and reloading, I've also tried another DVD drive all to no avail. 

Has anyone managed to install Prey using the DVD ? If so, how did you do it ?

---

### Post by Naiki Muliaina on 2010-08-20
Installed it like this :

[http://naiux.wordpress.com/2009/02/15/prey-on-ubuntu-installation-guide/](http://naiux.wordpress.com/2009/02/15/prey-on-ubuntu-installation-guide/)

I have the DVD version so it is possible to install via DVD. Need the download first of course. :)

---

### Post by BigSilly on 2010-08-20
I have the DVD version too. I just made the file executable (right click, permissions, mark as executable), then double clicked with the disc in place to install. I've literally just done it in fact.

My DVD drive is at dev/sr0. Could there be an issue there perhaps?

---

### Post by Naiki Muliaina on 2010-08-20
I will re install tonight, I have 2 DVD drives so I will try both and see if I get any problems.

---

### Post by Grenage on 2010-08-20
I installed mine in the same manner as Naiki Muliaina; that worked fine for me (DVD).

---

### Post by Raffles10 on 2010-08-20
I tried to install as specified in the instructions on the download page but the installer just doesn't seem to recognize the DVD. I tried using both DVD drives. I have Prey PC-DVD Rom VFC92121.

My DVD drives are /dev/sr0 & /dev/sr1 and I've had no trouble reading, ripping or burning CD's & DVD's with other applications. I also have symlinks /dev/cdrom & /dev/cdrom1 which link to /dev/sr0 & /dev/sr1, so I think the installer should detect it but it keeps expecting to find "Prey Disc 1".

I filed a bug at their website but I was surprised to find that it seems no one else is having this trouble.

---

### Post by Brebs on 2010-08-20
> **Raffles10 said:**
> symlinks /dev/cdrom & /dev/cdrom1 which link to /dev/sr0 & /dev/sr1
Good, but where are they *mounted*?

---

### Post by Naiki Muliaina on 2010-08-20
I installed, un installed, re installed with both drives perfectly fine. Click the link I posted and try that :)

---

### Post by alexandrius on 2010-08-20
i installed dvd version without any issues

---

### Post by Raffles10 on 2010-08-20
> **Brebs said:**
> Good, but where are they *mounted*?

The drives are mounted in /media/cdrom & /media/cdrom1

> **Naiki Muliaina said:**
> I installed, un installed, re installed with both drives perfectly fine. Click the link I posted and try that :)

This link provides the same information as: [Prey for Linux]("http://icculus.org/prey/")

---

### Post by Raffles10 on 2010-08-20
Oh well...I tried the obvious and downloaded the installer again, ran it and it worked. :tongue:

Guess I should've tried that before. :oops:

They were both downloaded from the same link and were both the same size 43mb, I don't know what happened with the first one.

---

