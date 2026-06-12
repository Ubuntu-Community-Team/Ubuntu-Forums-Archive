---
title: "cairo-dock --glitz - Undefined symbol: cairo_glitz_surface_create"
date: 2008-01-15
forum: Desktop Effects &amp; Customization
---

### Post by pinoytechie on 2008-01-15
This is what I'm getting when i run cairo-dock with glitz option: $cairo-dock --glitz
> symbol lookup error: cairo-dock: undefined symbol: cairo_glitz_surface_create

**ls show libglitz (and so as Synaptics)**
> /usr/lib$ ls *glitz* -l
lrwxrwxrwx 1 root root     21 2008-01-15 23:42 libglitz-glx.so.1 -> libglitz-glx.so.1.0.0
-rw-r--r-- 1 root root  19392 2006-07-11 02:00 libglitz-glx.so.1.0.0
lrwxrwxrwx 1 root root     17 2008-01-15 23:42 libglitz.so.1 -> libglitz.so.1.0.0
-rw-r--r-- 1 root root 151612 2006-07-11 02:00 libglitz.so.1.0.0


how to resolve this?

THANKS IN ADVANCE!

---

### Post by pinoytechie on 2008-01-22
help....

---

### Post by Borbus on 2008-02-16
I tried cairo-dock and I get this too.

---

### Post by SkiesOfAzel on 2008-02-19
You need a glitz enabled cairo to do that and AFAIK the cairo version that comes with ubuntu doesn't have it enabled.

---

### Post by northern lights on 2008-02-19
To use hardware acceleration with cairo-dock you must have a glitz-enabled libcairo. Download the following tarball [http://cairographics.org/snapshots/glitz-0.5.6.tar.gz]("http://cairographics.org/snapshots/glitz-0.5.6.tar.gz"). Extract it, open a terminal, navigate to the folder you extracted in (e.g. /home/user/glitz-0.5.6) and ./configure && make && make install:
```
cd glitz-0.5.6

./configure
make
sudo make install

cairo-dock --glitz
```

You should be off,

---

### Post by SkiesOfAzel on 2008-02-19
Actually glitz is already provided by ubuntu, cairo just doesn't use it. To enable it you just have to recompile it with that option.
```
mkdir cairo
cd cairo
apt-get source libcairo
sudo apt-get build-dep libcairo
sudo apt-get install fakeroot
cd libcairo-1.4.10
gedit debian/rules
```
Change --disable-glitz to --enable-glitz , save and close gedit.
Then
```
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i *.deb

```
Now you have to compile cairo dock with the --enable-glitz option when configuring and then start it with cairo-dock -g . It worked on my laptop but not on my desktop for some reason (the dock appears as a grey box).

---

### Post by Borbus on 2008-02-19
I did recompike my cairo to use glitz.

---

### Post by northern lights on 2008-02-19
> **SkiesOfAzel said:**
> Actually glitz is already provided by ubuntu, cairo just doesn't use it. Wasn't aware of that. I just remembered that back in the day when cairo-dock needed to be recompiled every time you wanted to add a launcher, it was vital to run it with some parameter like "no-glitz". Outta curiosity I tried to run mine with glitz and it produced the same error as posted here. I installed the above on my laptop - et voila: "cairo-dock --glitz" worked. Also looked not substantially better than before, so personally, I'm back to the regular version - certainly can't be less efficient.

> **Borbus said:**
> I did recompike my cairo to use glitz.And? What is it you wanna get across?

---

### Post by Borbus on 2008-02-19
And it still didn't work...

---

### Post by SkiesOfAzel on 2008-02-20
> **Borbus said:**
> And it still didn't work...
Which version of cairo-dock are you using ? The debs from [BerliOS]("https://developer.berlios.de/project/showfiles.php?group_id=8724") work just fine with glitz (i am using them right now).

---

### Post by Borbus on 2008-02-21
Well I built it myself. I'm not sure what I was doing wrong before but I just tried it again now and it works fine. Doesn't seem to be better with glitz, though. Not even as responsive as Y'z Dock on Windows.

---

### Post by northern lights on 2008-02-21
> **Borbus said:**
> Doesn't seem to be better with glitz, though

Told ya.

---

