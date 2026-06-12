---
title: "[SOLVED] upgrade killed gnome"
date: 2007-11-22
forum: Desktop Environments
---

### Post by jallain on 2007-11-22
When I logged on today there was one updae - gnome-system-tools v2.20.0. After installing this update, my screen froze and nothing worked except the power off button. When I logged on after restarting, all I get is a black screen with a mouse cursor. I've searched the forums and my problem was not resolved by some of the things I found. I went into the apt caache and reinstalled gnome-system-tools but it had all kinds of errors. Now I can at least login, but I have no active desktop. I can run programs (I'm doing so now) but no right click function on desktop (which is black). It seems that at least for me the update to gnome-system-tools killed my gnome. Other users have same problem. I can't roll back to previous version because dependencies fail. Anybody else experience this? Anybody have any suggestions how to fix without reinstalling? Thanks...

---

### Post by jallain on 2007-11-23
Solved:

I found a post where they issued the command

```
dpkg --configure -a
updated all packages
mv .gconfd to gconfd
mv .gconf to gconf

rebooted.
```

---

