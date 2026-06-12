---
title: "How to install XFCE4 on ubuntu server version"
date: 2006-06-02
forum: Desktop Environments
---

### Post by pradeep79 on 2006-06-02
Hi all, I am just wondering how to install XFCE4 on top of server version of ubuntu. I don't want the xubuntu-desktop package from the repository as it is too heavy. Tried doing sudo apt-get install xfce4 and installed only the xfce but it refused to start with an error message when starting  X server. Do you have to install X server separately before xfce4? When I updated the repository I also found other lightweight desktops like fluxbox and blackbox, but I am not sure whether you have to install X server separately. If I install the xubuntu-desktop there is no problem when starting and not X server error. Could someone tell me how to install a desktop on top of server version. I dont want to use gnome, kde or xfce that comes bundled with the distro.

---

### Post by john280z on 2006-06-02
pradeep79,
   I havn't had time to try xfce4 on top of Server yet, however I did try IceWm last night on Dapper Server and it worked OK:
[http://home.earthlink.net/~john280z/breezy-cd-min.html](http://home.earthlink.net/~john280z/breezy-cd-min.html)

   I did not do the "wdm" as I like to start X11 from the command line(startx).
I hope to have time this weekend to do an xfce4 install(not xubuntu).

johnm

---

### Post by ubnoobie on 2006-06-02
sudo apt-get install x-window-system-core xfce4

and if you want a light-weight display manager add: wdm (an xdm replacement)

---

### Post by IndigoMontoya on 2006-06-02
For my first install I did the minimal serve install and then  sudo apt-get install xubuntu-desktop

I thought xfce would be faster then gnome, but I saw no noticeable speed increase, so I actually then decided to install ubuntu-desktop.

---

