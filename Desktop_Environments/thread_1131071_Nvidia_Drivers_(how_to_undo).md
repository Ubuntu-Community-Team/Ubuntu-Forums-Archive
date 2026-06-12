---
title: "Nvidia Drivers (how to undo)"
date: 2009-04-20
forum: Desktop Environments
---

### Post by podollb on 2009-04-20
I've been bitten by changing my Nvidia driver before, so I'm asking this question in advance. When I'm notified of a new proprietary driver for my Nvidia card, and if I select to use it (via the GUI pop-up in Ubuntu), what are the steps I would need to do to UNDO this if I lost my X windows session? I'll still be able to use command line if it hoses up my X windows, but I'll need to know if I can merely just replace my xorg.conf file with the previous version or if more steps need to be taken. Thoughts?

---

### Post by cariboo on 2009-04-20
Make a backup of your current /etc/X11/xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
```

then if things don't work, you can start in recovery mode, remove all the nvidia files:

```
sudo apt-get purge nvidia*
```

and restart. you should get back to a default desktop, where you can go back to an older version of the restricted drivers.

Jim

---

