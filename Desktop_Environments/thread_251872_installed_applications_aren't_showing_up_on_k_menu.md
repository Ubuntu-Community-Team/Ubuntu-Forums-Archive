---
title: "installed applications aren't showing up on k menu"
date: 2006-09-06
forum: Desktop Environments
---

### Post by TommyMann on 2006-09-06
How do I get them to show up?

A few have been added, but some haven't.

For example Impress came installed but it's not on the menu.

---

### Post by aysiu on 2006-09-06
Right-click the KMenu and edit the menu and add an entry.

---

### Post by Jucato on 2006-09-06
or run this in Konsole:

```
kbuildsycoca --incremental
```

To refresh the K Menu. If the program is meant to have a Menu entry, it would appear. If not (like 3D Chess or 3D Desktop) you would have to add it manually like aysiu said.

---

### Post by TommyMann on 2006-09-06
I got this:

tommymann@tommymann-laptop:~$ kbuildsycoca --incremental
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
tommymann@tommymann-laptop:~$

---

### Post by TommyMann on 2006-09-06
Plus where do I find the programs to add them. I'm new to this Linux, and I don't understand the file system yet.

---

### Post by Jucato on 2006-09-06
I forgot to mention, ignore the error messages that it will spit out the first time you run that command. With or without the error messages, it will update you K Menu.

Most of the commands for applications you installed will be in /usr/bin/

---

