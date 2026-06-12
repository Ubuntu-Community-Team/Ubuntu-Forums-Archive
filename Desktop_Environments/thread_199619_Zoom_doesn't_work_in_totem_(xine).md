---
title: "Zoom doesn't work in totem (xine)"
date: 2006-06-19
forum: Desktop Environments
---

### Post by p_schott on 2006-06-19
After final release, I still have the problem mentionned here :

[http://ubuntuforums.org/showthread.php?t=137411](http://ubuntuforums.org/showthread.php?t=137411)

Zoom doesn't work in totem-xine with Dapper (it used to work in  with Breezy).

---

### Post by ashrack on 2006-06-19
it doesnt work 4M 2

---

### Post by ashrack on 2006-06-21
I've opened up a bug report here:
[https://launchpad.net/distros/ubuntu/+source/totem/+bug/50537/+index](https://launchpad.net/distros/ubuntu/+source/totem/+bug/50537/+index)

All of U who has these problems please confirm them in the bug report

---

### Post by ashrack on 2006-07-05
What am I the only one experiencing this issue??
All of U who experience the same issue please let me know and also sign the bug report here so the developers will fix this:
[https://launchpad.net/distros/ubuntu/+source/totem/+bug/50537/+index](https://launchpad.net/distros/ubuntu/+source/totem/+bug/50537/+index)

---

### Post by p_schott on 2006-07-05
I don't know why (can't remember about a totem update), but it appears that zoom feature now works fine for me. Perhaps there is a link with the graphic card driver, I struggled a while to get it working properly for my radeon 9200.

---

### Post by ashrack on 2006-07-05
tried it on 2 diff computers. One had NVIDIA the other had ATI and its the same on all

---

### Post by ashrack on 2006-07-09
Apperantly once I deleted 
'~/.gnome2/totem_config'
the zooming option started working again. For XINE or GSTREAMER backend.
BUt I find this very strange because when GSTREAMER backened is used the
'~/.gnome2/totem_config'
isnt even used!!!

---

