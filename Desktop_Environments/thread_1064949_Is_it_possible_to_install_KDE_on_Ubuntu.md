---
title: "Is it possible to install KDE on Ubuntu?"
date: 2009-02-09
forum: Desktop Environments
---

### Post by Adam N on 2009-02-09
Is it possible to install KDE in ubuntu because i found at the login that you can change your session and i was wondering if i could install KDE but also be able to use gnome as well.

Thanks in advance Adam

---

### Post by malspa on 2009-02-09
Yes, along with any other desktop environment or window manager.

---

### Post by ajgreeny on 2009-02-09
Easy, just do ```
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` to have all three major systems to look at and choose between at login.  Be warned, however, it will make your menus a bit jumbled and overwhelming unless you edit them and keep them down to a sensible layout.

---

### Post by Adam N on 2009-02-09
Thank you. I think that i will stick with gnome. Adam

---

### Post by gjoellee on 2009-02-09
> **ajgreeny said:**
> Easy, just do ```
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` to have all three major systems to look at and choose between at login.  Be warned, however, it will make your menus a bit jumbled and overwhelming unless you edit them and keep them down to a sensible layout.

That will install Kubuntu or Xubuntu, which is either Xfce or KIDE, but with a lot more (not needed) gadgets which makes it slower!

To install KDE:
```
sudo apt-get install kde
```

To install Xfce:
```
sudo apt-get install xfce4
```

---

### Post by ajgreeny on 2009-02-10
> That will install Kubuntu or Xubuntu, which is either Xfce or KIDE, but with a lot more (not needed) gadgets which makes it slower!
Agreed, but it will not give you the full experience of what kde in the ubuntu system is capable of, nor xfce.

---

