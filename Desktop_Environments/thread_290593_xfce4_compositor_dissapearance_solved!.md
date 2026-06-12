---
title: "xfce4 compositor dissapearance solved!"
date: 2006-11-01
forum: Desktop Environments
---

### Post by dswissmiss on 2006-11-01
Hi guys,
I've been trying to solve this problem ever since I upgraded to eft, but every thread I find regarding this problem is either abandoned or closed.

If anyone else is still having the problem of not having the compositor tab in window manager tweaks, follow this advice from Praxis over on the unofficial xubuntu forums (linked from xubuntu.com)

> Basically, go to WM Tweaks and change any setting. This should create a file with a bunch of settings:
~/.config/xfce4/mcs_settings/wmtweaks.xml

Change the value of 'Xfwm/UseCompositing' to 1, then log out and log back in.


---

### Post by trash on 2006-11-02
cool thanks! my compositor disappeared after turning it on then turning it off.

---

