---
title: "How to install optional GUI on Server ?"
date: 2011-11-16
forum: Desktop Environments
---

### Post by thyriel on 2011-11-16
Is there any way of installing (for example Xfce) as an optional GUI on a server that is running in console mode most times ?

Id tried around with a minimal Install and then installation via apt-get install xubuntu-desktop but that installs it along with an login manager and graphical stuff at booting :/

Id just want to install it so that i can start the X Server manually via startx when id need it...

Or is the only way of getting that making a minimal Installation of Xfce and installing all the programs by hand ?

---

### Post by jerrrys on 2011-11-18
I think you want xfce4 install instead of xubuntu-desktop

sudo apt-get install xfce4

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9#911)

---

### Post by vangop on 2011-12-27
If you want plain xfce, not xubuntu - check the [report]("http://ubuntu-answers.blogspot.com/2011/12/install-xfce-on-base-server-system.html") on that.

---

