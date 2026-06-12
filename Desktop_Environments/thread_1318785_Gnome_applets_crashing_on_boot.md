---
title: "Gnome applets crashing on boot"
date: 2009-11-07
forum: Desktop Environments
---

### Post by trx64 on 2009-11-07
Some applets (Deskbar and Indicator Applet) are crashing during boot with the message:

Panel encountered a problem with loading OAFIID:GNOME_<applet_name>

I've tryed:

- Uninstall (with purge) and install gnome-applets.
- Delete ~/.gconf/panel directory.
- Clear /tmp/
- Did it all again in text-mode, with X down.
- Some reboots

And nothing worked. Some idea?

---

### Post by trx64 on 2009-11-10
Nothing? The strange part is that it only happens in the boot. If I login into KDE and after in Gnome, all is right. If I login to Gnome and, after the error, give a:
$ killall gnome-panel
The panel comes back perfect. Any solutiuon?

---

### Post by trx64 on 2009-11-18
Someone? Up...

---

### Post by kg3000 on 2009-12-03
Hello, 

I'm experiencing a similar problem: [http://ubuntuforums.org/showthread.php?t=1343921&page=2](http://ubuntuforums.org/showthread.php?t=1343921&page=2)

Did you manage to resolve this issue?

Many thanks,

kg

---

