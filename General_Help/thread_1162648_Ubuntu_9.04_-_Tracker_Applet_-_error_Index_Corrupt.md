---
title: "Ubuntu 9.04 - Tracker Applet - error: Index Corrupted"
date: 2009-05-17
forum: General Help
---

### Post by Tictoon on 2009-05-17
Starting last night, I've been getting this error message that will not go away! The message looks like this:

[http://i245.photobucket.com/albums/gg79/tictoon/screenshot1-3.png](http://i245.photobucket.com/albums/gg79/tictoon/screenshot1-3.png)

So what should I do? They keep popping up no matter what I do. Should I just grab my important files and reinstall Ubuntu?

---

### Post by donato roque on 2009-05-18
I've been getting the same error message from tracker.  It seems to me like there's a bug with the application.  But I need indexing so I removed tracker and installed Beagle in its place.
You can kill the tracker applet including tracker itself.  If you go to terminal you'll notice tracker is eating too much cpu.

---

### Post by priscilla-jesus on 2009-05-18
I've been having the same error message. I followed the advice to uninstall tracker and install beagle, but I noticed that tracker will search and index the whole computer while  beagle just searches firefox.

---

### Post by Personatech on 2009-06-02
Priscilla,

Are you sure you didn't install just the Beagle Firefox extension?  Be sure to install "Search" under "Add/Remove..." as well which will, I believe, index everything on your system.

---

### Post by malrost on 2009-06-06
This appears to be a confirmed bug. [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560")

It had been happening to me as well, and started after I upgraded to 9.04. Jonaz's solution on the above link worked for me. In short:

1. remove the contents of ~/.cache/tracker, 
2. remove the contents of ~./.local/share/tracker/data. 
3. Reindex everything

---

