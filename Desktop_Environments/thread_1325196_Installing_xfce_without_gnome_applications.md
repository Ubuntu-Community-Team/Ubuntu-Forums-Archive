---
title: "Installing xfce without gnome applications"
date: 2009-11-13
forum: Desktop Environments
---

### Post by sakisds on 2009-11-13
I have kubuntu and i have installed icewm some days ago. Now i was trying to install xubuntu-desktop, that comes with a lot of gnome apps. I tried to install xfce4 package, but i only take a basic xfce without panels and stuff. So i am asking if there is anyway to install a full xfce without a lot of gnome apps(like media players, browser, some system tools that i already have with kubuntu).

---

### Post by Brandon Williams on 2009-11-13
Almost all of the gnome apps that come along with xubuntu-desktop are recommendations, not dependencies. You can get a full XFCE desktop with very limited gnome by installing without the recommends. This should do the trick:

```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

That said, when I look at the Depends for xfce4, it looks like you should have the panel, thunar, session manager, etc. It may be that you have to set these up yourself in order to get them to run automatically when you log in.

---

### Post by sakisds on 2009-11-14
It works fine, thanks a lot.

---

