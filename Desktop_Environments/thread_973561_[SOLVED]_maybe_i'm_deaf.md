---
title: "[SOLVED] maybe i'm deaf?"
date: 2008-11-06
forum: Desktop Environments
---

### Post by Rita G. on 2008-11-06
Ubuntu 8.10 w/gnome

can't get system sounds to work.

system>prefs>sound>sounds tab

entire page grayed out.

---

### Post by zarap on 2008-11-29
You are not alone ... I had the same prob after installing 8.10 ...
but I followed some advices from
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703)
and [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)
and have at least some of my system sounds back (still missing logout and trash).
What I did exactly was just:
add this repository in Synaptic: > deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main
reloaded and updated all installed packages named libcanberra
(The newest version of libcanberra is not in the official ubuntu - repos yet)
After the next start I was able to configure system>prefs>sound>sounds tab and had the sounds back.
good luck!

---

### Post by Rita G. on 2008-11-29
thanks zarap,

i've replaced it with mint since then.

same release (8.10) but everything works.

---

