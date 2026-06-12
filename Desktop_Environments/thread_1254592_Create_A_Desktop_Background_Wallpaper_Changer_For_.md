---
title: "Create A Desktop Background Wallpaper Changer For Xfce"
date: 2009-08-31
forum: Desktop Environments
---

### Post by carfield on 2009-08-31
I already create the wallpaper list file and it will change everything I logout and login. In order to make it able to change within the working session, most of the online tutorials suggest either:
```
 killall -USR1 xfdesktop
```
or
```
 xfdesktop --reload
```
But both are not really working... Anyone know how to trace?

---

### Post by carfield on 2009-09-02
OK, know the problem , using ```
killall -2 xfdesktop
```

---

