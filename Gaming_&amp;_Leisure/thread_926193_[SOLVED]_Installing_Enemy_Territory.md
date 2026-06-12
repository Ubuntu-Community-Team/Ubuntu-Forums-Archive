---
title: "[SOLVED] Installing Enemy Territory"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by xchecker on 2008-09-21
I am attempting to install Enemy Territory onto my Heron 8.04 box.  After launching the et-linux-2.60.x86.run file I get to an error in the installer which says I do not have permission to write to /usr/local/games/enemyterritory.  I am doing this as an admin user.

How do I overcome this?

---

### Post by Nettoyer on 2008-09-21
Just an educated guess:

sudo sh ./et-linux-2.60.x86.run

or
 
su -
(enter root pw)

then goto the location and run the file.

Alternatively.  You could try opening the file from the desktop, setting the properties to Let it run as a program and try it that way too?

Good luck.

Edit: Oh, btw, would it help if you manually make the directory for it?

---

### Post by xchecker on 2008-09-21
Got it thanks!  I was trying to open directly from the Desktop, but using sudo first from terminal worked better of course.

---

### Post by Perfect Storm on 2008-09-22
You want .deb package via synaptic add/remove - try PlayDeb

[http://www.playdeb.net/available_games.html](http://www.playdeb.net/available_games.html)

---

