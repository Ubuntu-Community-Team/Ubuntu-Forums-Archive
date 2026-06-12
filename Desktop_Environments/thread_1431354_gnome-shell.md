---
title: "gnome-shell"
date: 2010-03-16
forum: Desktop Environments
---

### Post by joachim10022 on 2010-03-16
How do I activate gnome-shell after downloading in ubuntu 9.10?

---

### Post by n0dix on 2010-03-16
See [this]("http://linuxandfriends.com/2009/11/18/how-to-install-gnome-shell-in-ubuntu-linux/") and [this]("http://anotherubuntu.blogspot.com/2008/11/installing-gnome-shell-in-ubuntu.html").

---

### Post by xtremesupremacy3 on 2010-03-16
Or, if like me your too lazy to read you could try this instead:

1) Turn off Compiz, if it's running

2) Press Alt+F2

and 3) Type 'gnome-shell' (Without quotes) And hit enter.

If you like what you see and want to keep this as default, simply turn off Compiz from Start-Up and add an entry for Gnome-Shell on Start-Up

---

### Post by joachim10022 on 2010-03-16
how can I turn to the normal Ubuntu desktop manager again? Or will it automatically start the default manager again after a reboot?

---

### Post by joachim10022 on 2010-03-16
> **xtremesupremacy3 said:**
> Or, if like me your too lazy to read you could try this instead:

1) Turn off Compiz, if it's running

2) Press Alt+F2

and 3) Type 'gnome-shell' (Without quotes) And hit enter.

If you like what you see and want to keep this as default, simply turn off Compiz from Start-Up and add an entry for Gnome-Shell on Start-Up

I am quite new in the Linux/Ubuntu enviroment. How do I turn off compiz?

thanks for your help

---

### Post by n0dix on 2010-03-16
If you have the compiz-fusion tray icon, there is a option to disabled the effects. If you don't installed compiz effects then go to the desktop, right click, the properties, Tab Effects and Disabled or None.

---

### Post by xtremesupremacy3 on 2010-03-16
> **joachim10022 said:**
> how can I turn to the normal Ubuntu desktop manager again? Or will it automatically start the default manager again after a reboot?

I'm sorry I didn't answer this sooner but:

If you haven't added it to your start up, then it will load into normal Ubuntu everytime you start the computer

---

### Post by navin.mistry on 2010-03-21
open gconf-editor

navigate to:

desktop->gnome->session->required_components

edit key 'windowmanager' to 'gnome-shell'

logout and login again, you should now be with gnome-shell..


Navin

---

