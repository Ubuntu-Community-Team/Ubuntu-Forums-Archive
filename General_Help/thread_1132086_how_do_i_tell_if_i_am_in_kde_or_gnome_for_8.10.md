---
title: "how do i tell if i am in kde or gnome for 8.10"
date: 2009-04-21
forum: General Help
---

### Post by tronnix75 on 2009-04-21
I do know if i am in the kde or gnome desktop? after 8.10 upgrade?

---

### Post by RedSingularity on 2009-04-21
KDE had the windows like look....with the menu button in the lower left corner.  Gnome has a panel bar on top and on bottom of the screen.

---

### Post by prem1er on 2009-04-21
If all he did was upgrade from an older version of Ubuntu shouldn't he still have whatever desktop manager was originally used?

---

### Post by tronnix75 on 2009-04-21
thank you for that but is there a way to see via command line or something to tell me and also how do i switch between the 2?

---

### Post by 3Miro on 2009-04-21
```

ps -e | grep kdm

```

If it returns nothing, then you are not running KDE.

ps -e checks for all the running processes and grep filters for the k desktop manager. For Gnome it is gdm.

It is not absolute, i.e. you may have two running is there are two people logged in at the same time, but it should work most of the time.

---

