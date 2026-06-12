---
title: "Switch desktop gnome to kde problem"
date: 2008-06-12
forum: Desktop Environments
---

### Post by steve3226 on 2008-06-12
Ubuntu 8.04 I installed the kde deskktop and set default to kde
/etc/X11/default-display-manager = /usr/bin/kdm

When I log in the kde desktop shows for a split second and then it quickly reverts back to the prior gnome desktop. 
 
The desktop icons for Firefox and Thunberbird show a small lock but they work to load the programs.

Can the gnome and kde files co-exist so I can switch from one to the other?

How can I use kde like I did the first time I installed the desktop over an existing gnome?

Steve

---

### Post by Xiong Chiamiov on 2008-06-12
Running
```

sudo dpkg-reconfigure gdm

```
will allow you to choose which login manager you use.  From there, you can choose which to login to, either GNOME or KDE.  Using gdm, change by clicking "sessions" in the bottom-left.  In kdm, choose options -> sessions.  From either you can then choose to start a new session and switch freely between them at will by using alt and some of the f-keys (for me, the first session starts at alt+f7, second at alt+f8 and so on).

---

