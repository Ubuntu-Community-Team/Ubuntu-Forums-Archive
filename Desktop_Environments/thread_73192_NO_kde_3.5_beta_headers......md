---
title: "NO kde 3.5 beta headers....."
date: 2005-10-08
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-08
I dont seem to have them ....Is there somewhere i can get them..?
Whe i try to ./configure anything i get this...


checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
roderick@ubuntu:~/Desktop/baghira-0.6c$

---

### Post by Knome_fan on 2005-10-09
Hi, did you install the dev packages?

If not, you probably need at least kdebase-dev and kdelibs4-dev.

---

