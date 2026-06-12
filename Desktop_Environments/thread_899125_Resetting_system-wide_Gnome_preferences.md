---
title: "Resetting system-wide Gnome preferences"
date: 2008-08-24
forum: Desktop Environments
---

### Post by tenbull on 2008-08-24
I'd like to reset some system-wide gnome preferences. This would include the theme, startup programs (sessions), what icons are on the taskbar (mozilla, evolution-mail, and ?), what is on the applications menu. Any help is much appreciated.

EDIT: does anyone know how to set system-wide booksmarks in firefox? ie, i want all my new users to have links to the eff in their bookmarks, any ideas?



And is it just me or does this guy look like he's taking hairstyling tips from Goku?:lolflag:

---

### Post by Benismyhorse on 2008-08-24
Open up terminal and enter:
sudo su

cd /home/USERNAMEHERE/
rm -r gconf gconfd

This will should reset all you panels

---

### Post by tenbull on 2008-08-24
I already know that, I want to make a new default panel though.

---

### Post by tenbull on 2008-08-25
bump

---

