---
title: "just installed ubuntu 5.10, need help using!!"
date: 2006-03-05
forum: Desktop Environments
---

### Post by joeintillamook on 2006-03-05
hi, i just installed ubnutu 5.10 off a cd from the ubunto site.  the install process went great.  the trouble is now at boot it loads fine then asks for my ubunto login, which works, then asks for my pass word, that also works great.  then it tells me that ubunto has no warranty, then it goes to this:  joe@ubuntu:~$ .  then when i type anything it goes to: -bash: command not found.  now my name is joe but i have no idea what iam suppose to type here any ideas.  thank you so much i would love to use ubunto soon!

---

### Post by Cephyr on 2006-03-05
Hm, that's funny. It seems to be booting into the "terminal" interface.

When you're logging in, there should be a button somewhere labeled "Session" Click it. Now choose the "GNOME" option. Next, log in normally.

This should put you into Ubuntu's normal desktop environment.

---

### Post by Sutekh on 2006-03-05
At the main installation screen did you just press Enter or did you type server/expert then Enter?

If you did a server install then you didn't install a desktop environment.  Now you will have to choose one to install.   You can choose GNOME, KDE or XFCE

Have a look at this site, and click on the Desktops at the bottom for some screenies on these environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME](www.gnome.org) - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE](www.kde.org) - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
```

If you want [XFCE](xfce.org) - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
```

These commands will install the respecitve desktops with most of the basic programs you will need.

---

### Post by towsonu2003 on 2006-03-05
it sounds like a problem with your video card not being configured by X. fron that $ promt, run ```
sudo dpkg-reconfigure xserver-xorg
``` and choose whatever looks right for your video card. once it is done, type ```
startx
``` to see whether X will launch succesfully. if not, post your video card specifications as well as those of your system, hoping that someone else is using that hardware as well. If you can, also attach /var/log/xorg.0.log (0 = zero) and /etc/X11/xorg.conf here. If you are dual booting with windows, there is a software you can install to browse and get those files from ubuntu: [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

ubuntu works out of the box with most hardware. it seems you will need some patience and ome effort (and luck) though...

---

