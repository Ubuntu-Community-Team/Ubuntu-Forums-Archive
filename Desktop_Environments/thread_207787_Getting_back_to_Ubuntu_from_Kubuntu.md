---
title: "Getting back to Ubuntu from Kubuntu"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Coomkeen on 2006-07-02
I used to have Ubuntu (6.06) after I decided to dump MSWindows.
All was fine. I could log in as root when something drastic needed doing.
Then I thought I'd try Kubuntu.
I don't see any great difference, except.. I can't log in as root any more.
It says it's 'not allowed'.
Not too keen on the 'new look' anyway, so...
Is there a way of getting back to Ubuntu?

Ron

---

### Post by aysiu on 2006-07-02
"Get back" meaning just to log into Gnome? Or "Get back" meaning to totally remove KDE from your system?

---

### Post by Coomkeen on 2006-07-02
Well I'm not sure.
When it was just Ubuntu the login allowed me to use root.
Now it's Kubuntu, and the blue Kubuntu screen appears with the login, it won't allow root, even if I select Gnome from the menu.

---

### Post by aysiu on 2006-07-02
Gnome's login screen manager is called GDM.
KDE's login screen manager is called KDM.

GDM's parameters and KDM's parameters are set separately. So if you tell GDM, "Allow a root user login," you'll have to separately tell KDM to allow one, too.

Or... just use GDM. Press Control-Alt-F1. Log in. ```
sudo /etc/init.d/kdm stop
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager_backup
sudo nano /etc/X11/default-display-manager
``` Change ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
``` Then save (Control-X, Y, Enter). ```
sudo /etc/init.d/gdm start
```

---

### Post by Coomkeen on 2006-07-02
Hey that's brilliant.
Very many thanks.
Leant a lot about the system as well.
Thanks again.
Ron

---

