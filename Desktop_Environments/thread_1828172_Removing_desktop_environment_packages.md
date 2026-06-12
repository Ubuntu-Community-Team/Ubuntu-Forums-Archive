---
title: "Removing desktop environment packages?"
date: 2011-08-18
forum: Desktop Environments
---

### Post by Tamalin on 2011-08-18
I have a desktop on which I installed Ubuntu 10.04 LTS, which I use as a file/print server.  I installed the regular desktop edition, not knowing exactly what I intended to do with it, but now, I really only let it sit, and occasionally access it via SSH;  I would install Ubuntu 10.04 Server Edition, but unfortunately the machine is getting too old for entirely new installs (I get cryptic warnings about hard drive errors when I try to install), and plus I would have to reconfigure everything.  So, my question is, is there a way to just remove the graphical packages, i.e., gnome, X, etc.?

Thanks

---

### Post by kellemes on 2011-08-19
Well.. if you're absolutely sure the server-packages you're depending on aren't making use of X.. I guess you can purge some core X-package like xserver-xorg-core.. it will remove X and the hole lot of packages depending on it..
And probably there are a bunch of other X-related packages you can remove.
Just to be sure I'd double check the list of 'to be removed packages' before hitting <ENTER>. You don't want to remove needed packages for your server.

Edit: It may help to also create a list of currently installed packages..
```
dpkg --get-selections > installed-packages
```

---

### Post by 3Miro on 2011-08-19
This tutorial tells you how to remove packages from various graphical environments (Ubuntu uses Gnome by default). Make sure you use the commands for 10.04 and not the latest 11.04.

You will also need to remove all of the Xorg stuff.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Note that if the HDD is failing, it will not be long before this machine becomes unusable. Backup everything important NOW and Consider getting a new HDD as soon as possible.

---

