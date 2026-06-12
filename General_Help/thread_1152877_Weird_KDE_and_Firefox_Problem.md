---
title: "Weird KDE and Firefox Problem"
date: 2009-05-08
forum: General Help
---

### Post by joeyknuccione on 2009-05-08
Recently installed KDE (alongside Gnome). My problem is when I close Firefox under KDE, and try to open it again, I get a "firefox is already running" error, even though I "quit" FF.

How can I fix this?
----------------------------
Much thanks, that did the trick.:guitar:

---

### Post by pantone186 on 2009-05-08
In a terminal type: top

look to see if firefox is running, if it is, on the left hand column you should be able to find a PID for the running program.

Open another terminal and type: sudo kill pid

where pid is the number identified from top, that should close the program

---

### Post by abyrne on 2009-05-08
or you can just type
```
killall firefox
```

---

