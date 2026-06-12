---
title: "No icons and unable to right on Desktop"
date: 2006-07-01
forum: Desktop Environments
---

### Post by abhishekp on 2006-07-01
I have a strange problem. I am unable to right click on the destop area and there are no icons on the desktop although I had put many icons earlier.

I got this problem when I installed xfce. When I logged into an Xfce session, everything was ok but when I again logged back into gnome I fount there were no icons on the desktop and the right click does not work. Please help.

---

### Post by aysiu on 2006-07-01
Try Alt-F2 ```
nautilus
```

---

### Post by BuBZ on 2006-07-01
I'm having this problem too. There are no icons on the desktop, it's not right-clickable and nautilus will not run. It started after dist-upgrading to the latest edgy and rebooting into the new kernel. Running nautilus in a terminal returns: ```
...
nautilus: symbol lookup error: nautilus: undefined symbol: g_type_register_static_simple

```
I'm guessing this has something to do with glib. I'm on edgy btw.

---

### Post by aysiu on 2006-07-01
Maybe this, then? ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

If you're using Edgy, maybe file a bug report:
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by BuBZ on 2006-07-01
"aptitude install ubuntu-desktop" did install some probably unrelated packages, but the problem still remains. I think it's something to do with Edgy.

---

### Post by dafthamster on 2006-07-02
I had the same problem just a few days ago on Xubuntu desktop.  After I installed VLC I had no right click menu or icons.

You can read the saga at [http://www.ubuntuforums.org/showthread.php?t=206590](http://www.ubuntuforums.org/showthread.php?t=206590)

To cut a long story short, the solution was simply to go to Applications -> Settings -> Desktop Settings and tick the little box labelled "Allow Xfce to manage the desktop".  Everything worked fine again after that.

I don't know how it got unticked, but it happened during the VLC installation.

Perhaps there is a similar setting in Gnome ... ?

---

