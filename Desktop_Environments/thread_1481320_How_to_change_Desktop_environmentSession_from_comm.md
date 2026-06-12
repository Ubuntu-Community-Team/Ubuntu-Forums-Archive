---
title: "How to change Desktop environment/Session from command line?"
date: 2010-05-12
forum: Desktop Environments
---

### Post by vussvillem on 2010-05-12
I had chosen automatic logon. Then updated to 10.04. During logout to change Desktop Environment/Session, I noticed that GDM login screen had an option for KDE session although I had not installed KDE. I got curious. So I tried it. System hangs. Restart does not help because somehow gdm proceeds to the KDE session although I did not choose it to be default session. So I had only CLI left.

I got over it by stopping gdm (/etc/init.d/gdm stop) and removing gdm and installing xdm. Anyway, what is the proper way? How to order desktop environment from CLI and/or where is the default desktop environment option written in a file?

---

### Post by x-shaney-x on 2010-05-12
Maybe run gnome-session from cli to get back into gnome then run gdmsetup once graphical?

Seems to be so many files related to GDM I wouldn't know where to look to edit it manually.

---

### Post by vussvillem on 2010-05-13
Thanks for the reply. I now ran gdmsetup in graphical environment (because Ubuntu 10.04 has abandoned "Login window" option in the menus) and disabled autologon to avoid accidental problems in the future. 

Your proposed solution is not bad. It led me to find information in Arch Linux forum. This is how one can do it. Running gnome-session alone will result in a: 

```
** (gnome-session:2563) WARNING **: Cannot open display:
```

Gnome requires X Windows System to run. Gnome-session command does not start X. So, what you have to do is to add *exec gnome-session* to your ~/.xinitrc, and then start X with the command startx.

But editing .xinitrc is a bit of a pain, if you're just experimenting with different window managers.

```
$ startx /usr/bin/gnome-session
```

---

