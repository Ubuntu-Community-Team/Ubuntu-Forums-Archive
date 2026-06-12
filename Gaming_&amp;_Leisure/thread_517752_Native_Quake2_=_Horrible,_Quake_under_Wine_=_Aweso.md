---
title: "Native Quake2 = Horrible, Quake under Wine = Awesome!"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by PrimoTurbo on 2007-08-04
I spent a good part of today trying to get Quake2 up and running, I have tried the repos, manual installation, and loki's installer, and bunch of other ports.

Most if not all (at least I haven't found 1), suffer from a number of problems.
Quake2 is not version 3.20 under linux, repos have some odd version, linux version is 3.21..
Mods like Action Quake2 don't work! Only part of the game data works correctly the rest doesn't load on +set game
Default gl based rendering engines kinda suck
Sound, sound and more sound problems and even when you finally get OSS to work with some parameters the sound slows the hell out of the game and you get like 20 fps.
Stuck in window mode for certain gl modes, mouse stuttering problems also.

With Wine and my Quake2 folder, I can run everything pretty well maxing out at 100+ fps. I'm not sure there might be slight mouse delay but it's very hard to really notice, I just feel a little odd but I'm getting used to it.

Just my 0.02, if you have had any other experiences with getting Quake2 to work please post. Also if you search the forum you will see people complaining about the same problems.

---

### Post by Sockerdrickan on 2007-08-05
I know! There is no freakin' good quake2

---

### Post by Brebs on 2007-08-05
There's Qudos, EGL, KMQuake2 and Quetoo. See [thread](http://forums.gentoo.org/viewtopic-p-3777588.html#3777588).

---

### Post by Sockerdrickan on 2007-08-05
This seems to be the by far best version [http://egl.quakedev.com/](http://egl.quakedev.com/)

---

### Post by Ferrat on 2007-08-05
> **PrimoTurbo said:**
> 
Quake2 is not version 3.20 under linux, repos have some odd version, linux version is 3.21..


This is probably the same reason as other Id games also has a "higher" version, something to do about the releases and some fixes ect. DOOM3 I know has this "diffirence" it's the same version but called diffirent dep. on OS

---

### Post by Sockerdrickan on 2007-08-05
EGL fails to build from svn

---

### Post by Brebs on 2007-08-05
See [EGL ebuild](http://bugs.gentoo.org/show_bug.cgi?id=152960) - convert it into a standalone BASH script ;-)

Anyway, I recommend [qudos](http://qudos.quakedev.com/) ([subversion](http://svn.quakedev.com/viewvc.cgi/qudos/trunk/)) as the best Quake 2 engine in Linux. Compile from **subversion** rather than the old QuDos-0.40.1.tar.bz2 tarball, for various improvements.

---

### Post by Sockerdrickan on 2007-08-05
Got any facelifts? (screens needed on that site!)

---

