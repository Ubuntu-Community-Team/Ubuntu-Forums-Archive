---
title: "Unable to edit start-menu"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Yoozer on 2005-10-25
I have a fairly odd problem: somehow, none of the changes I make using kdemenuedit are persistent (I can delete or cut entries and save all I want, but they just won't disappear, not even after a reboot). Now, this wouldn't really bother me if I knew where those entries are actually kept on disk so I could remove them manually, but, alas, I don't. Suggestions, anyone? :)

Thanks.

---

### Post by mlomker on 2005-10-25
KDE stores everything under ~/.kde

You can delete or rename that directory to reset all of your settings to default, if you wish.

---

### Post by beefsprocket on 2005-10-25
Sounds to me like a permissions problem. Could be that the menu file is read-only in general, or for your user specifically. Why not try chown out on the entire .kde directory? Can't hurt, and might fix it.

---

