---
title: "kde taskbar"
date: 2008-05-05
forum: Desktop Environments
---

### Post by cloudpersona on 2008-05-05
My taskbar disappeared, when I restart it pops up for a second and disappears again. any ideas how to fix this?

---

### Post by Zorael on 2008-05-05
What happens if you enter the following in a terminal? (Alt+F2 to get a run box, enter **konsole**)
```
$ kicker &
```
(Omit the dollar-sign, that's syntax convention to show it should be entered in a terminal.)

---

### Post by cloudpersona on 2008-05-05
thanks

---

### Post by Zorael on 2008-05-05
Of course, you can just run **kicker** from the run box; the terminal was simply there to see if it output any error messages.

---

