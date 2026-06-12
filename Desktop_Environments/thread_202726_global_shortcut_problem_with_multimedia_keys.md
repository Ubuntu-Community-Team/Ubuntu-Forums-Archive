---
title: "global shortcut problem with multimedia keys"
date: 2006-06-23
forum: Desktop Environments
---

### Post by matgates on 2006-06-23
When I set a global shortcut in KDE applications (e.g. amarok) it doesn't work if the key is a multimedia key and amarok is not in the foreground.

Other keys (e.g. win+c) are fine with amarok non-foregrounded, but for the multimedia keys on my keyboard it only works with amarok in the foreground.

The X keyboard layout is set correctly - xev shows the correct IDs for the keys (XF86AudioNext, XF86AudioPrev etc.)

I think the problem is broader than amarok.  I also used the KDE control center to set a global "input action" which opened the K menu when a global shortcut key is pressed.  This also worked fine for other keys, but not for the multimedia keys.

It used to work in Breezy.

Is anyone else having this problem, or have any idea about how to find out what is wrong?  My machine is a Dell Inspiron 8600.

-- 
Matthew Gates

---

