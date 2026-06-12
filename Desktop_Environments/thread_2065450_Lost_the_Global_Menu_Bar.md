---
title: "Lost the Global Menu Bar"
date: 2012-10-01
forum: Desktop Environments
---

### Post by gromacs on 2012-10-01
Hi, I installed Macbuntu but it turned out to be incompatible with 12.04, so I uninstalled it and it screwed up the Global Menu Bar. How can I fix it, and is there anything else Macbuntu screwed up that I should fix?

I tried to sudo apt-get the appmenu packages but it just tells me E: Invalid Operation. In the worst case scenario I'll just reinstall Ubuntu I guess.

---

### Post by ubume2 on 2012-10-04
Try unity --reset   from the terminal.

[S]Or else try 
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt

see:
[http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/disable-the-global-menu-in-ubuntu-12-04-precise-pangolin/)[/S]

---

