---
title: "About panel"
date: 2010-02-12
forum: Desktop Environments
---

### Post by Ashi2207 on 2010-02-12
hi my panel is gone how did i get back ?

---

### Post by RedSingularity on 2010-02-12
In a terminal try killing the panel like this

sudo killall gnome-panel

then............

gnome-panel to start it again.

---

### Post by mhgsys on 2010-02-12
If that didn't work then;

open a terminal and type:



```
gconftool-2 --recursive-unset /apps/panel
```

and restart gdm after that

 go to console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```

```
sudo /etc/init.d/gdm start
```

Panels should be back

---

### Post by Ashi2207 on 2010-02-13
> **RedSingularity said:**
> In a terminal try killing the panel like this

sudo killall gnome-panel

then............

gnome-panel to start it again.

 thanks its work

---

