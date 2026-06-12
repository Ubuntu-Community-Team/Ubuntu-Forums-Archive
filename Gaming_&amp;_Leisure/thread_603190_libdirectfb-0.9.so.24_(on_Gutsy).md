---
title: "libdirectfb-0.9.so.24 (on Gutsy)"
date: 2007-11-04
forum: Gaming &amp; Leisure
---

### Post by variableenigma on 2007-11-04
I've been trying to figure out how to play games on Ubuntu 7.10 (Gutsy), and so far I've had very little luck. 

Just as a little background info: I have installed the latest versions of Adonthell, Attal, Balazar, EgoBoo, (GNOME, Qt, X) NetHack, KQ, LostLabyrinth, The Mana World, and Widelands using the Add/Remove Application. I've also installed Tibia (both the Linux-native version and the Windows one with Wine), and Regnum Online and PlaneShift (using the Linux-native downloads).

I've determined that almost every game that I've tried requires a library called "libdirectfb-0.9.so.24". Now, the problem is that this library is no longer available (I've looked in Synaptic and around on the internet), and the new version, "libdirectfb-0.9.so.25", is apparently not an acceptable replacement for any of the games. 

So my questions are as follows:

Is there any way that I can update the games to accept the newest release of the library?

If not, is there any way to obtain this older file and install it on Gutsy?

And finally, is any one else having this problem? I feel alone in the world.. lol

Any help would be appreciated! 
Thanks in advance, 
Amanda

---

### Post by cogadh on 2007-11-04
Create a symlink to the new library with the name of the old library. Make sure you put it wherever the game is looking for it.
```
sudo ln -s libdirectfb-0.9.so.25 libdirectfb-0.9.so.24
```

---

### Post by dfreer on 2007-11-05
[http://packages.ubuntu.com/edgy/libs/libdirectfb-0.9-24](http://packages.ubuntu.com/edgy/libs/libdirectfb-0.9-24)

They do have 0.9-24 for edgy, but none for feisty or gutsy that I can tell. I'm not sure why nethack and the like would need 0.9-24, is 0.9-25 installed? Is your /etc/apt/sources.list missing any important entries?

---

