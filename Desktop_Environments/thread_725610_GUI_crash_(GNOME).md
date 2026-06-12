---
title: "GUI crash (GNOME)"
date: 2008-03-15
forum: Desktop Environments
---

### Post by ghost_ryder35 on 2008-03-15
So I am just surfing the net and then all of a sudden GNOME logs me out to a terminal and then automatically brings me back to the GUI logon window, I enter my name and password and everything is brought back to how it was when it crashed.  So I searched my logs and this is what I found.  **OS is Gutsy**

```

Mar 15 19:05:51 Ubuntu kernel: [ 1171.249788] printk: 5 messages suppressed.
Mar 15 19:06:00 Ubuntu kernel: [ 1179.371132] TKIP: received packet without ExtIV flag from 00:50:f2:cc:d2:12
Mar 15 19:06:03 Ubuntu kernel: [ 1183.021337] printk: 2 messages suppressed.
**Mar 15 19:06:05 Ubuntu gdm[5768]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 **
Mar 15 19:06:07 Ubuntu kernel: [ 1186.482455] printk: 1 messages suppressed.
Mar 15 19:06:14 Ubuntu kernel: [ 1189.435474] printk: 1 messages suppressed.
**Mar 15 19:06:14 Ubuntu gdm[7480]: WARNING: gdm_auth_user_add: /home/sopnpo/.Xauthority is not owned by uid 1000. **

```

How do I prevent this from happenning again?  What other logs could I check?

---

### Post by ghost_ryder35 on 2008-03-16
anyone?

---

