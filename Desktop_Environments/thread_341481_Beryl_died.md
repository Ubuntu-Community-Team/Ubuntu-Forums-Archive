---
title: "Beryl died"
date: 2007-01-18
forum: Desktop Environments
---

### Post by CoMRaDe_X on 2007-01-18
Well I was playing this game named tremulous, the game really wasn't running well and i was losing interest.  I go to the menu of the game and oh look, its illegible and i cant read it.  So i get sort of fed up with this all, and just decide to restart X (ctrl+alt+backspace) to forcibly leave the game.  Log back on and oh, looks like beryl window manager crashed (emerald) and it fell back to metacity (default).  So i go into the beryl manager and see if i can switch it back. It keeps crashing right as i switch it to emerald.  So i figure i corrupted some files or whatever so i reinstall the packages i used to get beryl working, (i used [this]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") guide to install) (I also did not reinstall the flgfx driver because my resolution seemed to be ok so that musnt be the problem).  The reinstall does not change anything.  At this point I am really confused although its not really a big deal that I'm using metacity it is still a bit degrading falling back.  Ive searched through my Xorg and nothing seems to be wrong, although you wouldn't think that restarting X would actually change any of my conf files.  If possibly you could steer me in the right direction that would be great.  Help would be appreciated, thanks

---

### Post by JamieC on 2007-01-18
Have you upgrade Beryl recently? A recent Beryl upgrade has issues, you might want to look at [this thread](http://ubuntuforums.org/showthread.php?t=341036&highlight=beryl).

---

### Post by CoMRaDe_X on 2007-01-18
ya just saw that, i did install upgrades today but i really didnt pay attension to what it was, any way to get a log of updated packages?

---

### Post by JamieC on 2007-01-18
There is no log for apt-get, there is for aptitude however (/var/log/aptitude). That is probably of no use though.

Your best bet would be to either hang in there for a fixed beryl upgrade or to downgrade to a previous version.

---

### Post by CoMRaDe_X on 2007-01-18
ok its working now, haha i really did think it had something to do with me restarting X real quick, but i guess not, thanks um sort of

---

