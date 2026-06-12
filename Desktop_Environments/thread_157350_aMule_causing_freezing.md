---
title: "aMule causing freezing"
date: 2006-04-08
forum: Desktop Environments
---

### Post by VitaminG on 2006-04-08
Whenever I launch aMule(2.3.0), it brings up the GUI and promptly freezes. It doesn't freeze Ubuntu right there, though. First, I use the force quit toolbar applet, which closes the window. If I watch in the system monitor, though, this doesn't kill aMule altogether. It does, however, take up ~60% cpu, and starts taking virtual memory at about 1-2 MiB per second. When this gets up to about 200 MiB, X and Gnome start to get starved for resources, and evrythingslows down, except aMule's resource consumption. At about 275-300 MiB, X and Gnome freeze completely, and I have to do a hard reset. This problem started just recently, I've been running aMule for almost 2 months without problems, until today. I tried reinstalling, and it didn't work. It was installed through Synaptic in the first place, but I reinstalled in command line(with apt-get), which should be just about the same. Thanks in advance for any tips.

Edit: Solved. I went into the $home/.amule/ directory and deleted the ed2klinks file. Apparently, aMule isn't too good at hadling these hashlinks, but saves them to load automatically anyway.

---

