---
title: "Since upgrade to Hardy, laptop crashes on fullscreen video"
date: 2008-05-17
forum: Desktop Environments
---

### Post by squiggly_crayon on 2008-05-17
Hi

I have recently upgraded to Hardy from Gutsy, via online update.
Since the update, my laptop crashes on fullscreen video. The problem is not specific to any player or to any video file type.

My laptop details:
Intel Centrino Duo core  @ 1.66GHz
RAM 1.5 GB
Graphics card: Intel Mobile 945GM (Integrated)

Please advice what to do since I cannot play any video in fullscreen.

thanks in advance

---

### Post by squiggly_crayon on 2008-05-18
I read thru some other posts and it seemed compiz can be a cause of problem.
I jst wanted to add that I do not have compiz installed either.

Please help asap.

---

### Post by ferretto on 2008-06-15
I have the same problem :(

---

### Post by zeus77 on 2008-06-30
same problem here, same graphics chipset.  i see these messages in /var/log/syslog:
```
WARNING: gdm_slave_xioerror_handler: Fatal X 
  error - Restarting :0
```

no idea how to debug this one.  what does your Xorg.conf look like?  mine is the stock Xorg.conf.

zeus77

---

