---
title: "No graphic yet"
date: 2006-08-12
forum: Desktop Environments
---

### Post by rejean on 2006-08-12
Hi all!
I just installed Diapper on a somewhat new machine (AMD XP 2000+ with a ProSavage DDR-K ( S3 Inc. 86835) video card. and for the first time it didn't give me a graphic after installing. 
I used to have a Penthium III AMD 500 GB with a S3 86325 ( Virge ) video card and I had no difficulty installing previous Ubuntu ( or Kubuntu) distros but this time I am puzzled.
I've tried "sudo dpkg-reconfigure xserver-xorg-core (or not core) or sudo apt-get install --reinstall xserver-xfreee86" but nothing similar ( with lots of variations ) has been successful so far. Any suggestion anyone?

---

### Post by aysiu on 2006-08-12
Maybe try this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm/ start
``` When you did *sudo dpkg-reconfigure xserver-xorg* before, did it appear to work?

---

### Post by rejean on 2006-08-12
It did try to do something but didn't achieve a lot. Will try your suggestions and let you know. Thanks a lot for the quick reply. Greatly appreciate it!

---

### Post by rejean on 2006-08-13
Good news. I managed to do a "sudo dpkg-reconfigure xserver-xorg" and I now have some graphics. I may have done a "startx" after that.

---

