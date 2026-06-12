---
title: "Xubuntu won't go away!"
date: 2009-03-25
forum: Desktop Environments
---

### Post by jliaci on 2009-03-25
Okay so I am new to Linux and my friend helped me install Ubuntu.  I had read about XFCE and wanted to give it a try.  So I downloaded the package and all went fine.  I was using it for a few days when i tried to run some programs that were giving me error messages.  It basically led to the window manager gettin messed up and applications not functioning properly. So in my newbie ways I simply tried to uninstall the package and figured i would reload it.  WRONG!  XFCE is still there.  I can still select it as a session and it works.  I uninstalled the package from package manager.  Tried removing using sudo apt-get autoremove xubuntu-desktop but it says package was already gone.  So I tried to reinstall and it still brings me back to the same messed up interface.  How do I completely gettin this environment off my hard drive.  Is there config files that go with it causing it to load up the same way? Also I have xubuntu apps making their way into the gnome drop down menus.  Not sure how or why. Any help would be appreciated.

---

### Post by Deathray on 2009-03-25
You can try this
```
sudo apt-get autoremove --purge xubuntu-desktop 
```

---

### Post by overdrank on 2009-03-25
You may look at Getting Back to a [Pure Gnome]("http://psychocats.net/ubuntu/puregnome")

---

### Post by jliaci on 2009-03-25
overdrank,

I used that website and their long list of packages to uninstall in the terminal.  I also used one or two other commands that i have found on the forums.  It gets rid of XFCE fine but the thing is is that there is some files left over somewhere.  I reinstalled it again and instead of a fresh install it just reinstalled all the packages I had just uninstalled with the same messed up settings.

---

