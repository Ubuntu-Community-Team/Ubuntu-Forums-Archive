---
title: "Reinstalling X/Gnome"
date: 2006-06-15
forum: Desktop Environments
---

### Post by binjured on 2006-06-15
Okay, to make a long story short I've kind of screwed up my Gnome/X configuration.  I tried a few different methods to install XGL and I think a couple of them conflicted and now I'm left with a buggy install (no Switch User screen, panels and windows turn black whenever my music player tells me what song is playing, etc.).  I want to get back to a clean slate and take it from there.  I tried simply reinstalling x-server-xorg (I think) and gdm, that didn't exactly do anything.  How do I make it basically like I just installed Ubunutu without actually doing that?

---

### Post by raptros-v76 on 2006-06-15
to reconfigure x back to its default, do sudo dpkg-reconfigure -phig xserver-xorg

---

