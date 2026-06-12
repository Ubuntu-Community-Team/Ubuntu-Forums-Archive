---
title: "top bar and bottom bar disappear  ??"
date: 2009-02-17
forum: General Help
---

### Post by chipheo83 on 2009-02-17
I'm a newbie. Please help me :)

When i logged in successfully. I only see desktop background and some icons. The top bar anh bottom bar disappear.

Please help me to fix this problem !

---

### Post by Greek on 2009-02-17
im also new with ubuntu, but i think its your resolution.
Try changing your resolution or use the resolution detect thingy.

---

### Post by geirha on 2009-02-17
Have you uninstalled any pre-installed applications? Evolution perhaps? Evolution is unfortunately very integrated with gnome, so uninstalling it will also uninstall parts of gnome (including gnome-panel). If this is the case, then hit Ctrl+Alt+F1 to get to a console, log in there, and install ubuntu-desktop with the command:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by UbuntuNerd on 2009-02-17
what happens when you hit alt+f2 ? the reason is maybe you don't have to install you desktop all over again like "geirha" said.

---

### Post by chipheo83 on 2009-02-17
> **geirha said:**
> Have you uninstalled any pre-installed applications? Evolution perhaps? Evolution is unfortunately very integrated with gnome, so uninstalling it will also uninstall parts of gnome (including gnome-panel). If this is the case, then hit Ctrl+Alt+F1 to get to a console, log in there, and install ubuntu-desktop with the command:
```
sudo aptitude install ubuntu-desktop
```

Thank you geirha, i have uninstalled evolution. I used your command and the problem is fixed :D

---

