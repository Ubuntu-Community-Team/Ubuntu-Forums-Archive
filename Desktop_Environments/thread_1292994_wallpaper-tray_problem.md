---
title: "wallpaper-tray problem"
date: 2009-10-16
forum: Desktop Environments
---

### Post by AnimeFreak on 2009-10-16
ok I am having a problem using wallpaper-tray

I don't see it in panel and I can't find any trace of it

I have ubuntu 9.04

and when I try to install a (.deb) file for it I get this error message:

>  Error: Dependency is not satisfiable: libboost-filesystem1.38.0 please help

thank you!

---

### Post by AnimeFreak on 2009-10-16
bump

---

### Post by AnimeFreak on 2009-10-17
please help

any answers will help

---

### Post by Shazaam on 2009-10-17
Right-click an empty space on one of your panels and click "Add to panel". You will find it there once you have it installed.
For libboost...
libboost-filesystem1.38.0 version is for Karmic (9.10).

[http://packages.ubuntu.com/search?keywords=libboost-filesystem&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=libboost-filesystem&searchon=names&suite=karmic&section=all)

A few ways to fix this...
1. You will need to get wallpaper-tray for Jaunty (9.04). You can do this through Synaptic or apt-get it in terminal.
2. Upgrade to Karmic (sort of not recommended on some machines as it is currently in Beta).
3. Look for a backport to Jaunty of the Karmic version (or a ppa).

---

