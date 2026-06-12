---
title: "Cannot see desktop"
date: 2010-09-08
forum: Desktop Environments
---

### Post by xbww on 2010-09-08
Just installed Ubuntu Server 10.04 on a fresh install of VMWare Player on Windows 7. When booted, I get a login prompt in console window. I can login but cannot see a desktop. I followed some instructions to install gnome-shell. Now when I type gnome-shell I get the following:
 
 
Error: unable to open display
Failed to start shell
*
KeyError: 'server glx extensions'
 
*I did not retype all of the traceback info but I can if it is needed. Just a lot to type :)
 
Thanks,
Brandon

---

### Post by NightwishFan on 2010-09-08
Ubuntu server does not incluce a GUI by default. You need to install one.
```
sudo apt-get install *
```
Replace the * with what desktop environment you want, such as ubuntu-desktop.

I also recommend installing gdm for a graphical log-in screen.

---

