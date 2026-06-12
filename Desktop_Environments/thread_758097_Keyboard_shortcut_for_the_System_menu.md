---
title: "Keyboard shortcut for the System menu"
date: 2008-04-17
forum: Desktop Environments
---

### Post by Talorgan on 2008-04-17
I have mapped my left Windows key to GNOME's Applications menu.

Is there any way I can map the right Windows key to the System menu?

---

### Post by Diabolis on 2008-04-17
I think that both keys count as only one, kind of having tow A keys. You can check this by disabling the windows key, then open a terminal and type **xev**. A samll window will appear, that window will catch all the input from your keyboard and mouse, so in the terminal you can see the name of each key. If both keys have the same name, then you won't be able of doing it.

---

### Post by Talorgan on 2008-04-19
... but Ubuntu makes a distinction between what it calls "Super_L" and "Super_R".

---

### Post by Diabolis on 2008-04-19
mmm since they are named different, maybe they can be used for different tasks, just give it a shot.

About the system menu, I don't its possible because the 3 menus count as only one object (applications,places,system).

If you want to use lots of key short cuts, maybe another window manager will suit your needs. When I want to use lots of keys for different tasks I use fluxbox. You can install it with:
```
sudo apt-get install fluxbox
```

You can have both gnome and fluxbox. At login screen you can choos which one you want to use each session.

In fluxbox key shortcuts are configured in a text file, so you can make ANY combination of keys start up ANY application.

---

