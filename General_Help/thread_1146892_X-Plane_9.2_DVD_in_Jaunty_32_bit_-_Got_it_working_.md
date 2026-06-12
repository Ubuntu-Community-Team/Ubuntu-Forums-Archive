---
title: "X-Plane 9.2 DVD in Jaunty 32 bit - Got it working finally!"
date: 2009-05-03
forum: General Help
---

### Post by emarkay on 2009-05-03
First, as of today (May 3) the filenames for the newest DVD installer and updater have spaces in them, which is a no-no in Linux, so rename them after downloading them!

Then, confirm you have all the "libopenall..." (3 packages) in Synaptic, and then,

"make a symbolic link from the old to the new library. In a terminal, run:

sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0"

FYI, here's the Bug link:
[http://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558]("http://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558")
[http://ubuntuforums.org/showthread.php?t=980976](http://ubuntuforums.org/showthread.php?t=980976)

---

### Post by surfed on 2009-05-13
> **emarkay said:**
> First, as of today (May 3) the filenames for the newest DVD installer and updater have spaces in them, which is a no-no in Linux, so rename them after downloading them!

Then, confirm you have all the "libopenall..." (3 packages) in Synaptic, and then,

"make a symbolic link from the old to the new library. In a terminal, run:

sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0"

FYI, here's the Bug link:
[http://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558]("http://bugs.launchpad.net/ubuntu/+source/openal-soft/+bug/273558")
[http://ubuntuforums.org/showthread.php?t=980976](http://ubuntuforums.org/showthread.php?t=980976)

It is better to follow these instructions as API has changed.
Download 32-bit libopenal0 deb, extract it and use libopenal.so.0 from there
[http://wiki.x-plane.com/8.10_Intrepid_Ibex]("http://wiki.x-plane.com/8.10_Intrepid_Ibex")

---

