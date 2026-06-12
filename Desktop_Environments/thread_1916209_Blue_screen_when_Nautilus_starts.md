---
title: "Blue screen when Nautilus starts"
date: 2012-01-27
forum: Desktop Environments
---

### Post by jpaulb on 2012-01-27
I an using Xubuntu 11.10 on a Dell XPS  8300
I have noticed that if I start Nautilus instead of Thunar my wallpaper is replaced with a blue background and the icons scattered across the desktop line up in order.

The reason to use Nautilus occasionally is to have a better access to Dropbox. Is there any way to have both?

---

### Post by sudodus on 2012-01-27
If you run
```
nautilus --no-desktop
```
it won't tamper with your desktop ('ignore the preference set in the preferences dialog' according to the man page).

---

