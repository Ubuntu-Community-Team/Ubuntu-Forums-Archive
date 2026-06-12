---
title: "login manager problem"
date: 2013-08-27
forum: Desktop Environments
---

### Post by pikapika-8-0 on 2013-08-27
Hi,
I rebooted a few days ago, and found that any login manager (lightdm or gdm) can't log me to any wm.
I had a log telling that gnome-shell segfaulted (which i don't use) and after removing gnome-shell and rebooting, i get "init: udev-fallback-graphics main process (1477) terminated with status 1" which may be not relevant.
The only solution I found was using startx in console, which works fine.
I have found nothing in X logs :
Xorg.1.log
"[ 60.052] Server terminated successfully (0). Closing log file."

ubuntu raring on imac with nvidia drivers

thanks

---

### Post by ibjsb4 on 2013-08-28
Try the repair commands, see if you get any clues.

```
sudo dpkg --configure -a

sudo apt-get -f install
```

---

### Post by pikapika-8-0 on 2013-08-28
hithanks for helping, though no packages are brokenI tried anyway without success

---

### Post by pikapika-8-0 on 2013-09-03
up ?

---

