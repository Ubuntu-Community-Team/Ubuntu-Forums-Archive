---
title: "New Tux Racer - now Planet Penguin Racer - how to install"
date: 2005-08-17
forum: Gaming &amp; Leisure
---

### Post by Rory on 2005-08-17
Hi,

Noticed today that Planet Penguin Racer is taking over from Tux Racer as the open source alternative.  
[http://entertainment.newsforge.com/article.pl?sid=05/08/09/147224&from=rss](http://entertainment.newsforge.com/article.pl?sid=05/08/09/147224&from=rss)

And it appears that most distros, including Debian via apt-get, have packages:
[http://projects.planetpenguin.de/racer/downloads.php](http://projects.planetpenguin.de/racer/downloads.php)

Any idea how I might be able to get PP Racer going on Ubuntu/Kubuntu?

Thanks,
Rory

---

### Post by arcanistherogue on 2005-08-17
Wow, this looks awesome.  I love TuxRacer, I want to know how to get this too.

---

### Post by Nightblade on 2005-08-17
I've got it running, just got it from CVS and compiled.

---

### Post by Rory on 2005-08-17
Yes, I've tried compiling from source but keep running in to dependency problems.  :(

Any idea how to go about getting a package built for an ubuntu repository so it is available, like it in in Debian/Fedora/SuSE/etc?

---

### Post by Nightblade on 2005-08-18
[QUOTE=Rory]Yes, I've tried compiling from source but keep running in to dependency problems.  :(

Any idea how to go about getting a package built for an ubuntu repository so it is available, like it in in Debian/Fedora/SuSE/etc?[/QUOTE]
I would but i have no clue how to do it :/

---

### Post by Hairy_Palms on 2005-08-18
the debian package works for me,

---

### Post by Jonah on 2005-08-26
Installing from the 0.3.1 source tarball, when I try to ./configure I get:
```
[...]
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
*** Hmm, you don't seem to have OpenGL libraries installed in the standard
*** location (/usr/lib).  I'll check in /usr/X11R6/lib, since
*** many distributions (incorrectly) put OpenGL libs there.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library
```
I have xlibmesa-gl-dev installed, so what am I missing?

Edit: Never mind. I installed the .deb, and it seems to work.

---

