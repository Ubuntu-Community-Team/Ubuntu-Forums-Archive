---
title: "ownership"
date: 2009-04-23
forum: General Help
---

### Post by penn2014 on 2009-04-23
im trying to edit a xconfig file but i cant because i need to open in root which is considered admin and i cant use it because for some reason im not admin


help???

---

### Post by michy99 on 2009-04-23
If you enter the following in Terminal, it will open up gedit as root.

```
gksudo gedit
```

---

### Post by stwschool on 2009-04-23
Or you can go gksudo nautilus to open the file browser as root. A quick way of entering a command (quicker than finding the terminal on the menu) is Alt+F2. It also means you dont get an extra terminal window clogging up your screen.

---

### Post by SuperSonic4 on 2009-04-23
If it happens to be the nvidia xconfig file there is ```
gksu nvidia-settings
```

---

### Post by CatKiller on 2009-04-23
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by penn2014 on 2009-04-23
My objective is to change my file xconfig in file x11 in file ect so that it will recognise my intel integrated graphics card

---

### Post by SuperSonic4 on 2009-04-23
```
gksu gedit /etc/X11/xorg.conf
```

```
gksu gedit /etc/X11/xconfig
```

---

