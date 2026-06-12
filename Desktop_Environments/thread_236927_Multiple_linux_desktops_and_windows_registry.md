---
title: "Multiple linux desktops and windows registry"
date: 2006-08-15
forum: Desktop Environments
---

### Post by sdebo on 2006-08-15
I read the forums and many members suggest trying multiple desktops to find one's favourite.
Having used windows for years now, I have grown allergic to the registry and the tendency for applications to leave files and traces behind after you uninstall them.

If I had to install multiple desktops/window managers in Linux (Dapper in particular) how do I make sure these do not conflict with one another?

If I decide to clear some disk space and remove any of them, how can I be sure that they do not remove some other application dependency?  How can I be sure that they will not leave unnecessary files behind them?  

To me knowing where a program starts and ends so that I can delimit it would be a huge bonus in Linux.  In windows I am (soon to be WAS hopefully) afflicted with having to format and reinstall windows once a year to get rid of a bulky registry.  

Thanks for enlightening me on the subject.

p.s. Under windows I use the excellent CCCleaner app, but it is not fool proof and it would be nice to know that there is no need for anything like it in Linux.

---

### Post by aysiu on 2006-08-15
There won't be a lot of conflict.

Mainly, you'll run into them all cluttering up your menus with tons of applications. That's about it.

If you use the gtk-qt engine, it's possible that KDE could "take over" the look of some of your Gnome applications, but there's a fix for that.

---

### Post by sdebo on 2006-08-15
I wanted to install only the desktop feel, not the whole lot.  I would like to check out konquerer but that is about it.  

If I decide to try something, and compile it with <make>, where does the executable go?  Do I need to move it to the bin folder?  What is the sbin folder for?  Sorry for these many questions.

---

### Post by aysiu on 2006-08-15
If you want to try out Konqueror, you don't need to install the KDE desktop at all. Just paste this command into the terminal: ```
sudo aptitude update
sudo aptitude install konqueror
``` Now you have it installed. Want to remove it? ```
sudo aptitude remove konqueror
``` If you're just trying out software, I'd highly recommend against compiling it.

---

### Post by der_joachim on 2006-08-15
The good news for you is that there is no such thing as a registry in Linux. Every system-wide setting is stored into a subdirectory called /etc. Everything in it can be opened in a text editor. Your personal settings are stored in /home/yourusername . In theory multiple desktops should not conflict with each other, because each desktop has its own config folder. 

Hope this helps. :)

---

### Post by sdebo on 2006-08-15
Thanks aysiu

der_joachim, so in theory uninstalling one application will just remove its folder under bin/sbin and etc.  Cool.

Only one thing remains unclear.  If I want to install the KDE desktop it means it will carry along all its applets and stuff across other desktops?  How can I choose to boot into KDE/Gnome/XFce distinctly so that I do not burden my PC unnecessarily?

---

### Post by aysiu on 2006-08-15
Actually, configuration files tend to linger, even if the application itself is removed. Just want to warn you (not that you'd even notice the config files unless you were digging for them).

And the services that load up with a desktop environment don't load up unless you're *using* that desktop environment. So when you log into XFCE, Gnome services don't load.

Now, one thing to keep in mind, though--if you load a Qt application in Gnome/XFCE or a GTK application in KDE, it may take a little bit longer to load, as it has to load in the appropriate libraries for that application to run.

---

### Post by sdebo on 2006-08-15
Thanks for all you help.

---

