---
title: "Confused"
date: 2011-11-10
forum: Desktop Environments
---

### Post by Atomic-Fanboy on 2011-11-10
Can someone explain to me the difference between "XFCE session" and "Xubuntu session", as well as the difference between "LXDE session" and "Lubuntu session"?

---

### Post by hhh on 2011-11-10
-edit- I just posted garbage by misreading the OP. I assumed you meant the difference between xubuntu-desktop and xfce or lubuntu-desktop/lxde, in which case the rest of this post is right. The package xfce4-session just provides session management (application autostart, splash screen) for the Xfce environment. /edit


This is starting to get asked more frequently. xubuntu-desktop and lubuntu-desktop pull in more packages than their counterparts to provide a more complete desktop environment, though installing just xfce4 or lxde will give you a working environment as well. To see the exact differences in, say, Oneiric, do a package search...
[http://packages.ubuntu.com/oneiric/xubuntu-desktop](http://packages.ubuntu.com/oneiric/xubuntu-desktop)
[http://packages.ubuntu.com/oneiric/xfce4](http://packages.ubuntu.com/oneiric/xfce4)

Normally, all the dependencies marked in red and green will be installed. If you want the leanest possible (but therefore less functional) install, you would, using apt in terminal, run...```
sudo apt-get install xfce4 --no-install-recommends
```

Also remember that the dependencies have dependencies of their own, so the list for xfce4 might show a dependency that xfce4-desktop doesn't because it's getting pulled in by another dependency.

---

### Post by Atomic-Fanboy on 2011-11-10
Thanks for explaining that :)

---

