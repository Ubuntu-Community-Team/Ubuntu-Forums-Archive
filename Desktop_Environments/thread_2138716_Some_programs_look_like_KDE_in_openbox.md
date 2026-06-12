---
title: "Some programs look like KDE in openbox"
date: 2013-04-25
forum: Desktop Environments
---

### Post by vitalix on 2013-04-25
Hi, guys.
I recently installed Openbox on Ubuntu 12.04. After a few additional settings it works just fine, but there is still one little problem.
All programs have the same gnome look, except for these ones: qBittorrent, everpad. They have KDE look.
I log in with pure Openbox, not Openbox/gnome or openbox/kde.
How can I fix it, and make them look like all others?

---

### Post by vitalix on 2013-04-25
any ideas?

---

### Post by Isamu715 on 2013-04-25
Try running *qtconfig* from the terminal and setting the widget style to "GTK+", Qt apps should adapt to the GTK theme then.

---

### Post by vitalix on 2013-04-26
that actually helped to change the style, but it coused another problem:
now some letter "i" in these programs apear like crossed rectangle (language - ukrainian)

---

### Post by zombifier25 on 2013-04-26
Try removing the hidden file .fonts.conf in your home folder.

---

### Post by vitalix on 2013-04-27
> **zombifier25 said:**
> Try removing the hidden file .fonts.conf in your home folder.

There is no such file, only folder ".fontconfig". I tried to replace it in another folder - Documents , but it did nothing.

---

### Post by vitalix on 2013-04-27
And also when i login into the gnome desktop env. everything works fine and all letters are there.

---

