---
title: "Desktop Icons"
date: 2011-05-09
forum: Desktop Environments
---

### Post by fjgaude on 2011-05-09
In unity natty 11.04, is there a way to stop partition or drive icons from showing on the desktop? They show in the launcher, that's fine, but is there a way to stop them from showing on the desktop?

---

### Post by matt_symes on 2011-05-09
Hi

Try this. From a terminal

```
gconftool-2 -s -t boolean /apps/nautilus/desktop/volumes_visible false
```Not sure if this will work in natty as i am currently in 10.04, so please report back if it does not.

Kind regards

---

### Post by fjgaude on 2011-05-09
Yes, it worked! Thank you!

I rebooted and it still worked.

---

