---
title: "Kde"
date: 2007-08-13
forum: Desktop Environments
---

### Post by XogGyux on 2007-08-13
Hello, im currently using Ubuntu 7.04 and i would like to know if i can install (and how) KDE desktop enviroment (beta4) without major issues and without installing Kunbuntu.:)

---

### Post by Happy_Man on 2007-08-13
It's easy enough (but be warned, KDE 4 beta is a beta and is VERY buggy). Just follow this guide: [http://kubuntu.org/announcements/kde4-beta1.php](http://kubuntu.org/announcements/kde4-beta1.php)

---

### Post by XogGyux on 2007-08-13
thanks you very much, i'll do it, uhm... that rule doesnt apply to Microsoft right? they really did a great job adding some new wonderful bugs to the final version not present in the beta. Anyways i like beta stuff
thanks!

---

### Post by XogGyux on 2007-08-13
i only found a cd image of kunbuntu. it is possible just to install KDE in my already existing ubuntu system (without unistalling ubuntu and/or installing Kunbuntu on top of ubuntu)?

---

### Post by bmartin on 2007-08-14
[quote=The page you were directed to]    * Ensure feisty-backports is enabled or you are running gutsy.
    * Install kde4base-dev.
    * These KDE 4 packages install to /usr/lib/kde4 so run:
          o export LD_LIBRARY_PATH=/usr/lib/kde4/lib
          o export KDEDIRS=/usr/lib/kde4
          o export PATH=/usr/lib/kde4/bin/:$PATH
          o export KDEHOME=~/.kde4
    * Run some programmes. Plasma seems to work and will run over kdesktop happily. Good luck.
    * To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.
    * To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.
[/quote]
That should do it.

---

