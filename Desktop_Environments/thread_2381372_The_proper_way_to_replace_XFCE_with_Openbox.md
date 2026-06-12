---
title: "The proper way to replace XFCE with Openbox?"
date: 2017-12-30
forum: Desktop Environments
---

### Post by defaults on 2017-12-30
Hello,

How does one replace the window manager in Xubuntu 16.04?

I'm setting up a new Ubuntu system for the first time in years and chose Xubuntu 16.04 as I want a long-lived minimalist setup. I've installed Openbox (which I've used for years) but I can't find anything related to swapping window managers in the XFCE system setting menus. There is a "LightDM GTK+ Greeter settings" item but it doesn't start anything. I've tried changing /etc/X11/default-display-manager from /usr/sbin/lightdm to /usr/bin/openbox, but that wasn't it (X wouldn't start at all and I couldn't even get a tty). The lightdm man page only pointed me to /etc/lightdm/ which has no configuration files.

---

### Post by vasa1 on 2017-12-30
Doesn't```
openbox --replace
```work for you?

---

### Post by defaults on 2017-12-30
All it does is change the window title bars into Openbox ones. I mean I want to *replace* the default with Openbox, not just run Openbox on top of it.

---

### Post by vasa1 on 2017-12-30
Have you got *openbox-gnome-session* installed? That should (I think) give you a choice of logging into an Openbox session.

---

### Post by defaults on 2017-12-30
I had that installed too... but I'm embarrassed to tell you I just found the session selection dialog. It opens from an icon in the top left of the login screen that I hadn't even noticed. Thanks for your replies!

---

### Post by Melodie on 2018-01-02
Hello, 

why not give a try to Bento Openbox? It's ready, not yet available in 16.04 but can easily be upgraded (you update first, reboot, then you do "sudo do-release-upgrade" and let go). The Xenial LTS will be built within a pair of weeks I hope.

[https://bentovillage.me/en/a-propos/](https://bentovillage.me/en/a-propos/)
[http://downloads.linuxvillage.org/](http://downloads.linuxvillage.org/)

you can get the idea with a full presentation when it was a RC : [https://linuxvillage.org/en/blog/2015/07/10/presentation-bento-trusty-rc2/](https://linuxvillage.org/en/blog/2015/07/10/presentation-bento-trusty-rc2/)

btw, it's less than 700MB&#8230; to achieve this last time, I left only Libreoffice Writer and Libreoffice Calc instead of the full LO suite, and removed one or two heavy apps. For the rest, you get most of everything which is needed. Also, if your computer has max 2 GB RAM and no nvidia, you can reinstall zram-config after install. (it's removed at post-install). If you have questions, feel free to ask! 

Best regards,
Mélodie

---

