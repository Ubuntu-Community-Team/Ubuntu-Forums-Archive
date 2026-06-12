---
title: "When running WOW 1 of my 2 monitors shuts off... why?"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by Gizim on 2007-07-27
Ok question - I have 2 monitors and when i run WOW with WINE the 2nd monitor shuts off and goes black which then allows the 1st monitor to go into full screen mode. Is there a way currently to allow both monitors to work at the same time? My Xorg.conf can be seen at [http://paste.ubuntu-nl.org/31546/](http://paste.ubuntu-nl.org/31546/)

---

### Post by Ferrat on 2007-07-27
My guess is that you either have clone mode or big desktop? 
Non of those will work when running 3D apps, you must run AFAIK two desktops, not sure if it's the same for nVIDIA but should be, try turning off twinview perhaps?

---

### Post by Gizim on 2007-07-27
> **Ferrat said:**
> My guess is that you either have clone mode or big desktop? 
Non of those will work when running 3D apps, you must run AFAIK two desktops, not sure if it's the same for nVIDIA but should be, try turning off twinview perhaps?

Its currently running in 3360x1050 instead of Twinview what should i put in instead of Twinview?

---

### Post by Ferrat on 2007-07-27
Hmm you should have two desktops atleast that's what I prefer, not sure how to set that up working good with nVIDIA but I think there might be a guide somewhere in these forums. 

Thing is that the 3D layer overlaps all the others but the program only sends rendering to one of the screens and the other one goes black, if you got clone mode you can have the same 3D grafics on both but that doesn't help much, with two seperate desktops you can jump between them and do lots of fun stuff :)

---

### Post by OoooMatron on 2007-07-27
maybe try  xinerama instead of twinview.

---

### Post by brnz on 2007-07-28
I'm currently running Cedega with WoW on dual screens. 
Also running twinview.

I don't get this issue with WoW running.
But I had to setup WoW with the monitor I wanted to use first -then turned the other monitor back on (just backed up my xorg.conf to xorg.conf.dual - then did a setup for the main screen)

Poof - working WoW with dual monitors - oh.. I run WoW windowed so I can pop to the other screen to do whatever...

---

