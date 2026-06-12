---
title: "Black screen after KDE 4.5 upgrade"
date: 2010-12-11
forum: Desktop Environments
---

### Post by cand!de on 2010-12-11
I'm under Kubuntu 10.04 and I upgraded kde from 4.4 to 4.5. via apt-get.
After KDM login, I got a black screen with the mouse cursor visible and active. I have no idea how to fix the problem.

I tried this :


```
sudo apt-get install -f
sudo dpkg --configure -a
sudo reboot
```with no effect.


KRunner (ALT+F2) doesn't open.


Can anyone provide me some guidance ?

---

### Post by franik4ever on 2011-02-02
Try disable Compositing by ALT + SHIFT + F12

---

