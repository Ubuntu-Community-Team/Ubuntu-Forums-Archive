---
title: "How to have xset executed at login (before opening any terminal)"
date: 2016-11-27
forum: Desktop Environments
---

### Post by f(fanta) on 2016-11-27
I would like to set the mouse acceleration with something like
```
xset m 3/1 10
```
and I would like it to be executed right after I login, i.e. even before I open any terminal; therefore .profile or .bashrc don't cut it. I have tried to write it in a file named .xsessionrc in my home, but it did nothing. I am using Unity.
Thanks!

---

### Post by ian-weisser on 2016-11-27
/home/$USER/.config/autostart runs at login.

---

