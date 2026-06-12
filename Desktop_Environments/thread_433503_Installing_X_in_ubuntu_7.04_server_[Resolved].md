---
title: "Installing X in ubuntu 7.04 server [Resolved]"
date: 2007-05-05
forum: Desktop Environments
---

### Post by zymofyt on 2007-05-05
I just installed ubuntu 7.04 server, and when finished realized that it comes without X. I tried installing it by using:

sudo apt-get install x11-common

This doesn't seem to be enough, I keep getting an error 3 and the message "No such file /etc/X11/X" and then "Cannot contact X server". Apparently I haven't gotten all of X installed?

Coulld you advise me what I need to do to install X fully using apt-get?

I have the machine c onnected to the internet, so no problem there. I have installed kde and GNOME as well, but need the basic X to make it work.

---

### Post by aysiu on 2007-05-05
Aren't KDE and Gnome a bit heavy for a server? Try this: ```
sudo apt-get install xorg icewm
startx
```

---

### Post by zymofyt on 2007-05-05
>Aren't KDE and Gnome a bit heavy for a server?

Not this one - it's only going to run httpd and postfix. Plenty of power left.

Thanks for the suggestion, it worked. :-)

---

