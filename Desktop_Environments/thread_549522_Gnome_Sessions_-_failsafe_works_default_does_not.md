---
title: "Gnome Sessions - failsafe works default does not"
date: 2007-09-12
forum: Desktop Environments
---

### Post by olmecnz on 2007-09-12
When I logon under my normal default session into gnome under ubuntu it hangs or sometimes not but the windows don’t have any borders or grab handles.

If I use failsafe gnome session to logon, everything works perfectly. Do you have any idea where session settings are stored? What I would like to do is overwrite my default session with the failsafe one. Or, make the failsafe one the default one by other means if that is possible.

---

### Post by toby_1_kenobi on 2007-10-20
This is exaclty what I need to do as well. Did no-one answer your question? How did you solve this problem?

---

### Post by L0rd_D4rk on 2007-10-21
I also have the same problem, I upgraded from feisty, what about you?

---

### Post by damotor on 2007-10-21
Try disabling xgl:
```
cd .config/xserver-xg/
touch disable
```
or
```
apt-get remove xserver-xgl
```

Cheers.

---

