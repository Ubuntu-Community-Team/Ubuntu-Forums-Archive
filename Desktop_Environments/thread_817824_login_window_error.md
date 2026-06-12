---
title: "login window error"
date: 2008-06-04
forum: Desktop Environments
---

### Post by AnLGP on 2008-06-04
It says this "GDM (GNOME Display Manger) is not running.  You might be using a different display manager, such as KDM, CDE login, or xdm.  If you wish to use this feature your system will need to be configured to use GDM instead".

When I try to change my sessions to log into fluxbox it's not there.  There's only "openbox" (which I've never installed), and some other ones.  Also which I've never installed.  I used to be able to change to the fluxbox one but now I can't :(

Please someone help!  How do I configure my system to use GDM so I can change the login session to fluxbox?  Thanks!

---

### Post by Inxsible on 2008-06-04
Go into recovery mode and type in ```
sudo apt-get install gdm
``` Once its installed, type in```
sudo /etc/init.d/gdm start
```That should start gdm and you will be able to login.

As to why it shows Openbox and other WMs I have no idea. But you must have installed them and that's why they are there.

---

### Post by AnLGP on 2008-06-04
chuckles.  as it were i hosed my install and can't even do that now.  please read here:

[http://ubuntuforums.org/showthread.php?t=818479](http://ubuntuforums.org/showthread.php?t=818479)

maybe you can help?

---

