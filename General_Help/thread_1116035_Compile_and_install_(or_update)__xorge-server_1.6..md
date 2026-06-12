---
title: "Compile and install (or update?)  xorge-server 1.6.0 with Hardy 8.04"
date: 2009-04-04
forum: General Help
---

### Post by Kelen.Chang on 2009-04-04
i found xorg-server has released version 1.6.0, but Hardy 8.04 staying in 1.4.0. so, i want to compile and install (or update?) xorg-server 1.6.0 manual. but i never do this before, so i have no idea about this. is there any idea or suggestion for me?

---

### Post by taurus on 2009-04-04
Any reason why you need to upgrade the version in repos with the latest one for hardy?

---

### Post by dtoronto on 2009-04-04
It's not a great idea to upgrade on a distro version that works well with the current packet version.  I believe you can install it with

sudo apt-get install xorg-server-1.6.0

---

### Post by Kelen.Chang on 2009-04-04
> **taurus said:**
> Any reason why you need to upgrade the version in repos with the latest one for hardy?

i guess it's better performance than this one. so i wanna try..

---

### Post by Kelen.Chang on 2009-04-04
> **dtoronto said:**
> It's not a great idea to upgrade on a distro version that works well with the current packet version.  I believe you can install it with

sudo apt-get install xorg-server-1.6.0

There is no package xorg-server-1.6.0 in my source. which one should i add?

---

### Post by Nepherte on 2009-04-04
I recommend you just leave it be. xorg-server is a very complicated package which involves updating many other packages. On top of that, you might be in for a surprise as there are a lot of changes like the way it handles input devices. If you insist on having xorg-server 1.6 I suggest you wait for jaunty.

---

### Post by Kelen.Chang on 2009-04-04
actually, i always staying in some problem. 
when i watching movie or playing games, the screen has little flicker sometimes. (running compiz).

---

### Post by taurus on 2009-04-04
> **Kelen.Chang said:**
> actually, i always staying in some problem. 
when i watching movie or playing games, the screen has little flicker sometimes. (running compiz).

And does it still flicker if you turn compiz off?  What makes you thing the new X server version wouldn't have the same problem?

---

### Post by Kelen.Chang on 2009-04-04
Well, i saw someone has same problem with me before he install X server 1.6.0. but he is use archlinux. so i want get a try.

---

### Post by markbuntu on 2009-04-04
Xserver 1.6.0 also needs Xorg 7.4 which I think needs kernel 2.6.28 and all the video drivers will need to be upgraded along with alsa and all the other kernel modules and everything that depends on them.

I really think you will get stuck in a dependencies loop since so many packages will need to change. This could totally bork your system so be aware of that.

---

### Post by Kelen.Chang on 2009-04-04
I was in kernel 2.6.29.1 and offical nvidia 180.44 right now.

---

