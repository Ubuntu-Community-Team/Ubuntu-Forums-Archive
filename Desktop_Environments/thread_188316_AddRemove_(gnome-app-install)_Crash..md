---
title: "Add/Remove (gnome-app-install) Crash."
date: 2006-06-03
forum: Desktop Environments
---

### Post by Monster_user on 2006-06-03
Whenever I run Gnome-app-install (Applications -> Add/Remove), it crashes. It does so, just after it finishes checking the available applications list. As soon as the progress bar gets to 99%.


Here is the console output.

```
 gnome-app-install
Introspect error: The name org.freedesktop.AppInstall was not provided by any .s ervice files
no listening object (The name org.freedesktop.AppInstall was not provided by any  .service files)

** (gnome-app-install:7799): WARNING **: return value of custom widget handler w as not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop
Segmentation fault
```

---

### Post by Antman on 2006-06-03
Have you tried uninstalling the package via Synaptic and reinstalling?

---

### Post by laroetman on 2006-06-04
Mine crashes too.  So does Synaptic.  The window loads fine, but if I try to add or remove a program, it just says "... Is not available in any software channel.  The application might not support your system architecture".  It says that for all.  If I try to run Synaptic, it crashes and says "Could not download all repository indexes".  One of my roomates is having the exact same problem.  He did use the same CD as I, but everything else seems to work fine.  Any ideas?

---

### Post by Monster_user on 2006-06-04
[QUOTE=Antman]Have you tried uninstalling the package via Synaptic and reinstalling?[/QUOTE]
I have. Apt-get, dpkg, Synaptic, and the Update program work fine. Only Add/Remove is affected.

---

### Post by frank_castle on 2006-11-27
I have the same problem. Only Add/Remove (gnome-app-install ) does not work.

well, i temporarily solved it by linking /usr/bin/python to usr/bin/python2.4, not python2.5. now, it works fine.

---

### Post by tbonepower07 on 2007-03-15
I have the exact same problem.  gnome-app-install crashes as soon as the progress bar completes.  Interestingly, so does automatix, but not Synaptic.

I'm a newbie, so can you explain in more detail how to link to the older version of python?

Thanks

---

### Post by Monster_user on 2007-03-18
Actions -> Run -> gksu nautilus

Then browse to "/usr/bin/". It may take a few minutes to load, so be patient.

Then click on any file, and quickly type "pyt", or find the "python" file. Right-click it, and select "Properties". You should be able to change the target of the link to "/usr/bin/python2.4".

---

