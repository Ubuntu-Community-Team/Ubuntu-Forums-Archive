---
title: "Unity, KDE, Gnome, Top Menu also on the Window?"
date: 2012-09-06
forum: Desktop Environments
---

### Post by iaw4 on 2012-09-06
Unity:

Is it possible to display the top menu also on the window frame itself?  (I don't want to remove the top bar menu [necessarily].)

I am blessed with a 24" display, so I would be quite happy to give up a little more screen space for the mouse convenience.

/iaw

---

### Post by ensignavenger on 2012-10-13
I don't know if it is possible to have the menu display both on the top (Called the Global Menu) and on each window, but you can disable the Global Menu and make the application menu appear on each window, which is what I did.  

Two ways:

Install **Unsettings** from the software center, under Windows, turn the global menu off.

**OR**

Use the following command from the terminal to remove the Global menu-

```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

---

### Post by iaw4 on 2012-10-17
this would make a great feature for larger screens IMHO.  it would obviate the discussion whether it is better to have them in one place or the other.

unity-developers---are you listening?

/iaw

---

