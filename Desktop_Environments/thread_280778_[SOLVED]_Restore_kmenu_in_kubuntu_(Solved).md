---
title: "[SOLVED] Restore kmenu in kubuntu? (Solved)"
date: 2006-10-19
forum: Desktop Environments
---

### Post by Bastanteroma on 2006-10-19
I deleted my system menu in Kubuntu and now I want it back.  Does anyone know how to restore the default menu rather than rebuilding it by hand?

---

### Post by Bastanteroma on 2006-10-20
Anyone know how to restore the kmenu to its original state?  I deleted the system menu and a bunch of other stuff that I want back.

---

### Post by aysiu on 2006-10-20
Try pasting these commands in the terminal: ```
mv ~/.config/menus/applications-kmenuedit.menu ~/.config/menus/applications-kmenuedit.menu.messed.up
killall kicker
kicker
```

---

### Post by Bastanteroma on 2006-10-21
Like a charm.

Thanks

---

### Post by Chal on 2007-12-21
thhhhhhhhhaaaaaaaaaaaankkkkkkkkkyou!

deleted nearly all progs in kmenu and adding them per hand was impossible

did what you wrote before and every entry is back!

---

