---
title: "how to edit/change GDM&amp;splash"
date: 2009-04-17
forum: Desktop Environments
---

### Post by hawkingyy on 2009-04-17
1. How can i change the GDM theme in Terminal?
2. How can i show splash screen while without install GNOME Splash Screen Manager in Terminal??
thanks !

---

### Post by PacSci on 2009-04-17
To change the GDM theme in terminal, run:

```
sed 's|GraphicalTheme\=.*|GraphicalTheme=YOURTHEME|' /etc/gdm/gdm.conf | sudo tee /etc/gdm/gdm.conf
```

Replacing YOURTHEME with the theme name, of course.

---

### Post by hawkingyy on 2009-04-18
> **PacSci said:**
> To change the GDM theme in terminal, run:

```
sed 's|GraphicalTheme\=.*|GraphicalTheme=YOURTHEME|' /etc/gdm/gdm.conf | sudo tee /etc/gdm/gdm.conf
```

Replacing YOURTHEME with the theme name, of course.

thanks a lot !
and if the GDM Theme is a tar.gz package, and where should i put it and install it ??

---

