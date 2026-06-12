---
title: "Help! KDE won't start!"
date: 2005-08-15
forum: Desktop Environments
---

### Post by gingermark on 2005-08-15
Ok, so the only think of note I've done recently was try to install a firewall. I installed Firestarter, but it was too complicated, so uninstalled it, and tried Guarddog, but it kept crashing, so I uninstalled that too.

My computer was being slow, so I logged out of KDE into XFCE, but it didn't help, so I tried to log back into KDE.

It started up normally saying:

> Setting Up Interprocess Communication

but then said:

> The following installation problem was detected while trying to start KDE:

      No write access to '/home/gingermark/.ICEauthority'

KDE is unable to start

Another window then popped up saying > Could not start ksmserver. Check your installation. I was then sent back to the KDM log in screen.


I tried logging into GNOME and XFCE but got even less from them, with both just sending me back to the KDM log in screeen.

Any help would be greatly appreciated.
gingermark.

---

### Post by Beire on 2005-08-15
[QUOTE=gingermark]Ok, so the only think of note I've done recently was try to install a firewall. I installed Firestarter, but it was too complicated, so uninstalled it, and tried Guarddog, but it kept crashing, so I uninstalled that too.

My computer was being slow, so I logged out of KDE into XFCE, but it didn't help, so I tried to log back into KDE.

It started up normally saying:



but then said:



Another window then popped up saying  I was then sent back to the KDM log in screen.


I tried logging into GNOME and XFCE but got even less from them, with both just sending me back to the KDM log in screeen.

Any help would be greatly appreciated.
gingermark.[/QUOTE]
 i'm not a pro but try this:

```
sudo chmod 777 /home/gingermark/.ICEauthority
```

---

### Post by gingermark on 2005-08-15
Thanks so much! That worked a treat!

---

