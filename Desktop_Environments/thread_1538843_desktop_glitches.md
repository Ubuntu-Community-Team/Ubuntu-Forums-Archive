---
title: "desktop glitches"
date: 2010-07-25
forum: Desktop Environments
---

### Post by supadupadad1 on 2010-07-25
when i start my computer there is usually some graphics that are not right. sometimes the shutdown icon in the right corner is not there and my user name is there twice. other times i have two wi-fi and battery icons. Why does this happen? And how do i fix it? Thanx

---

### Post by wojox on 2010-07-25
Try resetting your panels:

```
gconftool --recursive-unset /apps/panel
```

```
pkill gnome-panel
```

---

### Post by supadupadad1 on 2010-07-26
thank you. i haven't tried it yet but will the next time it happens. will that be a temporary fix of should it fix the problem from now on? also every time i shut down ubuntu 10.04 i get a fail message that says check  system diagnostics. what do i need to do? how do i check it and fix the  problem?

---

### Post by supadupadad1 on 2010-07-26
ok. i just tried it and it did fix my panel. but i have a feeling it will do it again. is this a common issue? and how do i fix it perminently?

---

### Post by Baba-Juju on 2010-08-23
I have the same glitch. It happens randomly so far. Should be filled as a esthetical bug.

---

