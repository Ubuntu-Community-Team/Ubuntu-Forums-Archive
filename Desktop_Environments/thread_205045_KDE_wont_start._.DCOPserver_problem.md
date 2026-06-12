---
title: "KDE wont start. ./DCOPserver problem"
date: 2006-06-27
forum: Desktop Environments
---

### Post by weasel fierce on 2006-06-27
so I try to boot into KDE, and I get an error reading:
could not read network connection list
/home/weasel/.DCOPserver_ubuntu__0

Gnome seems to be working fine

---

### Post by Thirsteh on 2006-06-27
This might be an indication that someone, or something, has been CHMOD'ing the file in question lately. Check it's attributes and modify as necessary. 0664 should work fine, ultimately, use 0777.

---

### Post by weasel fierce on 2006-06-27
here's the crazy thing though. This file doesnt even appear.

---

