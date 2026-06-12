---
title: "qt3/settings"
date: 2009-01-29
forum: General Help
---

### Post by Razvanica on 2009-01-29
Hello all,
I am trying to use an application developed under Suse 10 on my ubuntu 8.04.
The application demands qt3 libraries and headers so I have installed libqt3-mt-dev and qt3-dev-tools packages. The compilation went like a charm and I can use 90% of the application. For the other 10% I need to copy a file in the qt3 settings folder. The application's user guide says this folder should be placed under /usr/lib/qt3/etc/settings/ but in my /usr/lib/qt3/ I only have a plugins/ folder. As the user guide also indicated that my qmake.conf file could be found under /usr/lib/qt3/mkspecs/ when its real location was /usr/share/qt3/mkspecs/, I thought I should take some precaution and ask you for advice. 
So, my question is, does the settings folder has a different name on ubuntu? Or do I have to install another package for it? Or should I just create the folder manually?
Thanks.

---

### Post by idunavailableforadi on 2009-02-26
I'm also facing some problems with this qt3 directory not having the specified mkspecs directory. Could anyone suggest a solution?

---

