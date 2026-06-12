---
title: "can imake ISO using my ubuntnu 8.04?"
date: 2009-03-01
forum: General Help
---

### Post by abhilashm86 on 2009-03-01
i want an ISO file of ubuntu because i'm trying installing ubuntnu on a pen drive flash(4 gigs),
i actually have ubuntu in dvd,its 3.7 GB, can anyone tell how to do ISO image or i need to download?please suggest anything?
i can't download fast as i have 512 kbps speed

---

### Post by razy60 on 2009-03-01
Use unetbootin, i have 8.10 on a 1Gb stick which works fine.

heres the link:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Raz

---

### Post by heindsight on 2009-03-01
If you have the CD or DVD you could put the disk in your drive and then do:
```
dd if=/dev/cdrom of=Ubuntu.iso bs=1024
```

---

### Post by abhilashm86 on 2009-03-01
> **razy60 said:**
> Use unetbootin, i have 8.10 on a 1Gb stick which works fine.

heres the link:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Raz

hey after booting using flash drive, can i install some applications like audio players and some IDE's?

---

### Post by abhilashm86 on 2009-03-01
> **heindsight said:**
> If you have the CD or DVD you could put the disk in your drive and then do:
```
dd if=/dev/cdrom of=Ubuntu.iso bs=1024
```

hey i don't have ubuntu.iso but a install dvd of ubuntu 8.04(3.7 gb), so only i asked whether its possible to convert this to .iso image?

---

### Post by heindsight on 2009-03-01
> **abhilashm86 said:**
> hey i don't have ubuntu.iso but a install dvd of ubuntu 8.04(3.7 gb), so only i asked whether its possible to convert this to .iso image?

the .iso stands for ISO9660, the filesystem used on CDs and DVDs that dd command I gave, will make an exact copy of the disk in your CD drive and save it as a file called Ubuntu.iso. Thus, after the dd command completes, the file Ubuntu.iso will contain an ISO9660 filesystem image.

EDIT:
In other words, you do have an ubuntu iso image, it is burned into your ubuntu DVD, that dd command I gave will copy it from the DVD to a file on your hard drive...

---

### Post by abhilashm86 on 2009-03-01
> **heindsight said:**
> the .iso stands for ISO9660, the filesystem used on CDs and DVDs that dd command I gave, will make an exact copy of the disk in your CD drive and save it as a file called Ubuntu.iso. Thus, after the dd command completes, the file Ubuntu.iso will contain an ISO9660 filesystem image.

EDIT:
In other words, you do have an ubuntu iso image, it is burned into your ubuntu DVD, that dd command I gave will copy it from the DVD to a file on your hard drive...

ok now i understood, but when i executed your command, it took a long time, should i wait for longtime to do this task?
 
ok fine, where will ubuntu.iso be saved??i need the path:)
thanks for the iso details, i was too dumb before:)

---

### Post by razy60 on 2009-03-01
> **abhilashm86 said:**
> hey after booting using flash drive, can i install some applications like audio players and some IDE's?

If you go to the link i suggested it will give most of the info you need, Essentialy it is a live cd on a stick with a few more options, so yes it will do most of what you want. ~If you want to store items then you need a larger storage device to make it truly portable.

Raz

---

### Post by abhilashm86 on 2009-03-01
> **razy60 said:**
> If you go to the link i suggested it will give most of the info you need, Essentialy it is a live cd on a stick with a few more options, so yes it will do most of what you want. ~If you want to store items then you need a larger storage device to make it truly portable.

Raz

yea the link is really good, i was just looking at it, i'll surely try and reply:)thanks

---

### Post by heindsight on 2009-03-01
> **abhilashm86 said:**
> ok now i understood, but when i executed your command, it took a long time, should i wait for longtime to do this task?

Yes, it will take some time, just wait for it to finish.

> **abhilashm86 said:**
> 
ok fine, where will ubuntu.iso be saved??i need the path:)

the file will be saved in the directory where you were when you ran the dd command. If you just opened a terminal and ran the command, then it should be in your home directory.

---

