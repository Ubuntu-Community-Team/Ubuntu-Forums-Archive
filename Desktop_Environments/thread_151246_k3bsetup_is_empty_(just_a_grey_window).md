---
title: "k3bsetup is empty (just a grey window)"
date: 2006-03-27
forum: Desktop Environments
---

### Post by Bomper on 2006-03-27
K3B says that cdrdao will be executed without the superuser privileges. And that's right that k3bsetup is empty (just a grey window):


This problem is due to a wrong .desktop file for k3bsetup2.

I'm afraid i'll have to admit this is due to the patch merged from Ubuntu that 
adds "NoDisplay=False" to the desktop file.

     gedit /usr/share/applnk/Settings/System/k3bsetup2.desktop

  adds "NoDisplay=False"


BUGS:

        [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=353826](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=353826)

---

