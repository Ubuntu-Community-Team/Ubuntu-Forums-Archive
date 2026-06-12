---
title: "Installing brlcad 7.10.4 on ubuntu 6.06  with emc 2.2"
date: 2009-01-21
forum: General Help
---

### Post by rayj0007 on 2009-01-21
[FONT="Courier New"][SIZE="4"][/SIZE][/FONT]
First post to forums and a nub at Linux.  I am trying to install BRL-CAD on the ubuntu 6.06/emc 2.2 distribution from linuxCNC.org.

1st: It doesn't install in the "/usr" directory per the manual. It installs in "/home/cnc/Desktop/BRL-CAD/usr/brlcad/rel-7.10.4/bin/"

2nd: When I try to run "mged" using "./" in the above directory I get the message "error while loading shared libraries: libtermio.so.19: cannot open shared object file: no such file or directory"

The file libtermio.so.19 is in the directory: "/home/cnc/Desktop/BRL-CAD/usr/brlcad/rel-7.10.4/lib"

Any help greatly appreciated

rayj0007

P.S. I found an acceptable work around. I installed 2 different versions of ubuntu, one for each application.

---

