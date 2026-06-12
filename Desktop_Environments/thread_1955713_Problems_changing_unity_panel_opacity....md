---
title: "Problems changing unity panel opacity..."
date: 2012-04-10
forum: Desktop Environments
---

### Post by try1211 on 2012-04-10
Hey, I've been using Ubuntu 11.10 since its release yet I haven't run into this issue before:

So I reinstalled Ubuntu 11.10, but I never liked the global menu thing, so I did the usual with that:

```
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt
```

then I installed CCSM to customize unity but when I go to set the opacity on the unity top panel it doesn't work. 

Even when the values for the panel opacity are set to 0.0100 in CCSM the panel looks like it does in the attached screenshot.

I did some experimenting and discovered that the opacity values worked when I reinstalled the global appmenu packages, and then the same thing when I, again, uninstalled them.

So, from the looks of things, the problems seems to be stemming from the global appmenu, but I have no idea what it is thats conflicting with my panel opacity...

Any ideas?

...Oh, and the panel flashes white when shuhtting down or logging off with the appmenus disabled and opacity set in ccsm, it never did that before either...

---

### Post by manoyth on 2012-04-20
I have the same problem too. When logging out or shutdown the global menu shows as in your screenshot. If you make the top panel fully transparent or not transparent, the problem is solved. I haven't found other solution yet. I hope that after upgrading to Ubuntu 12.04, it will be fixed.

---

