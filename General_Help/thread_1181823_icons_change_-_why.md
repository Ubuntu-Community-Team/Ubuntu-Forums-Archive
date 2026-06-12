---
title: "icons change - why ?"
date: 2009-06-08
forum: General Help
---

### Post by UBUminJ on 2009-06-08
Sometimes, the appearance of Ubuntu 08.10 changes - why ?
e.g. there is a life-belt for the help icon and sometimes there is a different icon - the life-belt state seems to be abnormal

also the colors of the menubars and the colors of the document icons are different
normal: brown-orange (if I remember well)
not normal: some kind of greenish gray

what happens ?

thank you
Michael

---

### Post by UBUminJ on 2009-06-08
I have attached screenshots of what I consider normal and what abnormal.

---

### Post by Rallg on 2009-06-08
I also noticed this happen from time to time in 8.10. Rebooting usually restored the expected theme. In any case, I never noticed any change in functionality. (I am now in 9.04.)

Presumably, during boot, some settings file is mis-read (maybe a race condition) and an alternative theme is used instead.

---

### Post by CatKiller on 2009-06-08
Sometimes the gnome-settings-daemon, which applies your themes and whatnot, doesn't start for some reason, so you get the default Gnome theme. You can either log out and log back in, or run gnome-settings-daemon manually from the (Alt-F2) Run dialogue.

---

### Post by Soul-Sing on 2009-06-08
It happens here on jaunty now and then.
a change from a customized theme to human-clearlooks.

edit: random

---

