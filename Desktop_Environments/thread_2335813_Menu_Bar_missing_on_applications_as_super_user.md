---
title: "Menu Bar missing on applications as super user"
date: 2016-09-01
forum: Desktop Environments
---

### Post by bart-burroughs-cox on 2016-09-01
When opening an app like gedit as sudo the menu bar is not available so there is no way to do anything except save the file under the existing name or exit. any idea how to fix the issue? no menu bar appears for any application. Nautilus, Gedit etc.:(

---

### Post by mook765 on 2016-09-01
You should not use GUI-based applications with sudo. Use "gksudo" instead.```
gksudo nautilus
gksudo gedit
```

---

### Post by bart-burroughs-cox on 2016-09-02
doesn't make a difference. Using gksudo to start the program does not provide the menu bar.

---

### Post by howefield on 2016-09-02
Are you using the Unity desktop and do you get menus as a normal user ?

```
echo $XDG_CURRENT_DESKTOP
```

---

