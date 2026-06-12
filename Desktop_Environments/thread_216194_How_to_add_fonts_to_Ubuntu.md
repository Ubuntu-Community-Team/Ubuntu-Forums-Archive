---
title: "How to add fonts to Ubuntu"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Viet Tux on 2006-07-15
Hi

I am using Ubuntu and Windows XP

I want to add some fonts in Windows Xp to Ubuntu

How to add ?

Thanks

---

### Post by ayoli on 2006-07-15
a way is to copy the .ttf files you want to /usr/share/fonts , then refresh the font cache by type in a console:
```
sudo fc-cache -f -v /usr/share/fonts
```
edit: putting in /usr/share/fonts make this fonts accessible by all users on your box, if you want a user install you put them in ~/.fonts and run fc-cache on ~/.fonts instead of /usr/share/fonts
regards.

---

### Post by Viet Tux on 2006-07-15
Thanks

I want all app display use fonts I assign

How to ?

Thanks

---

### Post by ayoli on 2006-07-15
go to menu: System>Preferences>Fonts and pick font you want for desktop/apps/window titles
regards.

---

