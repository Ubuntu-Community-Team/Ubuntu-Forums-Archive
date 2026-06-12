---
title: "accidentally delete default panel"
date: 2011-06-12
forum: Desktop Environments
---

### Post by hpng on 2011-06-12
Hello:

Machine:  Ubuntu 10.04 LTS, AMD64

i have accidentally deleted menu on the default panel.  now there is only
Firefox icon on the panel.
hoe do I restore the default panel?

thanks.

---

### Post by nzjethro on 2011-06-12
To restore the menu, right click the panel, select "Add to menu", and click "Main Menu". Else to restore all gnome panels to default, run
```
$ gconftool-2 --recursive-unset /apps/panel 
$ pkill gnome-panel
```

---

### Post by hpng on 2011-06-12
Solved.

---

### Post by nzjethro on 2011-06-12
Wicked. Wanna flag the thread solved so others know it is so? Click Thread Tools up the top, and click Mark as Solved.
:D

---

