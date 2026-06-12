---
title: "vncserver + xfonts trouble"
date: 2006-01-08
forum: Desktop Environments
---

### Post by vitalic on 2006-01-08
Hello everybody,

Im relativily new to the Ubuntu releases and only installed Breezy a couple of days ago. Im having a known problem with installing vncserver (with gnome desktop) and ive read up a lot of topics, but the solutions just don't seem to work for me.

My vncserver logs kept whining about default font paths and stuff, I manually made a fonts folder in /X11R6/lib/X11/fonts and copied the files from /usr/X11/lib/fonts into it. This removed some errors but not 'speedo' for example. 

I also tried these fixes that i found on the forum, but they didn't seem to work for me:
sudo dpkg-reconfigure xserver-xorg 

&

sudo ln -s /usr/bin/mkfontscale /usr/X11R6/bin
apt-get remove xfonts-base
apt-get install xfonts-base
startx

After days of editing vnc.conf, trying command lines fixes, xstartup editing and even a fresh ubuntu install, I finally managed to get a somewhat working gnome desktop, but its kind off distorbed as you will see by the screenshot:
[http://img203.imageshack.us/my.php?image=gnome8xe.jpg](http://img203.imageshack.us/my.php?image=gnome8xe.jpg)

Does anybody know the solution, cause its driving me nuts tbh

---

