---
title: "kde desktop lockup"
date: 2006-06-04
forum: Desktop Environments
---

### Post by harty83 on 2006-06-04
My desktop under KDE is locking up randomly when I right click on a file.  Everything will work except the desktop.  Icons disappear, right click doesn't work, etc.  Panels, applets, and programs all still work though.  I deleted .kde thinking that would fix it but I just locked up again.  I don't have any system processes going out of wack.

What "program" operates the desktop of KDE?  Is anyone else having this problem?

Thanks.

Edit: correction.  When I open konqueror and right click on a file, it locks up.  This is all while the desktop is locked up.  What operates the right click menu?  What would cause the lockup?

---

### Post by Jeff Eklund on 2006-06-04
I don't know whats causing the lock-up, but I experienced something similar with KDE 3.4. The program drawing the deskto is called kdesktop and you could kill it in a terminal by typing killall kdesktop. I don't know if that will kill the window manager too, but in that case, KDEs window manager is called kwin. Hw do you know if your Windowmanager died? Well, all open windows loses their borders and you can'tmove them around anymore. Really annoying.
Hope you find a soilution!

---

### Post by jaanus on 2006-07-26
It appears that in my case a similar problem was caused by Kopete. 
After installing Kopete 0.12.1 desktop doesn't freeze any more. If you don't want to do that, try disabling Autoaway in Kopete.

---

