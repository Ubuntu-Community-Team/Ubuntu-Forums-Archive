---
title: "Gnome game question."
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by Chief1 on 2007-06-15
My wife has taken over my Ubuntu machine and she's hooked on Same Gnome, that ball dropping game. If I were to try Kbuntu or Xbuntu to learn more, would I be able to use this game out of the Gnome environment?
Thanks in advance.

---

### Post by Garyu on 2007-06-15
Yes, that should be possible, just as you can use any KDE application in gnome. You can have KDE, Gnome and XFCE installed on the same machine. just do

sudo aptitude install kubuntu_desktop xubuntu_desktop

and there you go, you can choose which desktop to log into in the GDM. All of the programs should be on the menu.

The menus will probably be very cluttered though, so you would have to do some menu editing to make it nice and clean.

---

### Post by MenZa on 2007-06-15
Yes. All applications can be run in any desktop environment despite which you use.

And Garyu, the packages are *kubuntu-desktop* and *xubuntu-desktop*.

I suggest running *ps ax | grep same* (or *game* or similar) while the game is running to find out what the actual name of the process is, so you can start it from the terminal.

---

### Post by DoktorSeven on 2007-06-15
**sudo apt-get install gnome-games**

---

