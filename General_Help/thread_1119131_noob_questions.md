---
title: "noob questions"
date: 2009-04-07
forum: General Help
---

### Post by ddguevara on 2009-04-07
I am sorry if these are too basic, i-ve looked everywhere and solutions are mostly for something different.


My situation is that I installed eclipse 3.4 manually and also installed eclipse 3.2 using the package manager. 

My first problem: I don't want eclipse 3.2, but the package manager installed about 10-20 dependency packs along eclipse, Im trying to un-install them all, but I don't know how to do this without having to do it manually one by one.

My second problem: I want to have an icon of eclipse on the task bar, but...  I am trying to drag it directly to the task-bar and it takes me to the menu for the custom application launcher. This forces me to select an icon from a library, instead of just taking it from the application I am selecting. Is there a way to do this like windows xp where you just drag it and forget, or do I have to search for a custom one.

Thanks
David G

---

### Post by mb_webguy on 2009-04-07
For the second part, you should be able to right-click on the panel and select Add to Panel->Application Launcher, and select the application to create the launcher.

For the first part, it's always better to install from a repository rather than a deb file, and from a deb file rather than from source.  Add the [Eclipse PPA]("https://launchpad.net/~eclipse-team/+archive/ppa") to your Software Sources to install the latest version of Eclipse and get automatic updates as they're released.  To remove the version of Eclipse you compiled from source, you'd need to download the same source again, and use "./configure; make; sudo make uninstall".

And for future reference, if you're going to compile something from source, it's a good idea to use [checkinstall]("https://help.ubuntu.com/community/CheckInstall"), which creates a deb from the compiled source and installs the software from that.  This allows you to manage the software from one of the several package managers (i.e. Add/Remove, Synaptic, apt-get, etc.).

---

