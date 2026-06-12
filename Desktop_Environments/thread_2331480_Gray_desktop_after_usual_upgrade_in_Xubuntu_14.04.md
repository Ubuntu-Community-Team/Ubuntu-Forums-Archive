---
title: "Gray desktop after usual upgrade in Xubuntu 14.04"
date: 2016-07-22
forum: Desktop Environments
---

### Post by atipico on 2016-07-22
After an update a couple of days ago, my desktop is gone and a gray screen is now in it's place. No usual icons and if I try to click with the right mouse button nothing happens. However, the top menu is functional. Following a tip, I installed the last "xfdesktop" version, just as bellow:

xfdesktop --version
This is xfdesktop version 4.12.2, running on Xfce 4.12.
Built with GTK+ 2.24.23, linked with GTK+ 2.24.23.
Build options:
Desktop Menu: enabled
Desktop Icons: enabled
Desktop File Icons: enabled

My OS details:

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

uname -a
Linux atpc 4.2.0-42-generic #49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Any light? Thanks a lot.

[IMG]http://s.mlkshk.com/r/199U0[/IMG]

---

### Post by &amp;KyT$0P# on 2016-07-22
What happens if you run these commands in a Terminal?

This one makes sure xfdesktop isn't running
```
xfdesktop --quit
```

and this one tries to start xfdesktop
```
xfdesktop --disable-wm-check
```

---

### Post by atipico on 2016-07-22
Well it comes back just fine. however, when I restart it turns gray again...

---

### Post by atipico on 2016-07-23
Although the problem persisted after the restart, it seems that after the last Xubuntu base new upgrade the bug was solved. Thank you.

---

