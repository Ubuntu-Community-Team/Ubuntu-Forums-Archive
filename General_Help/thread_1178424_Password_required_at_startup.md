---
title: "Password required at startup"
date: 2009-06-04
forum: General Help
---

### Post by luigifonti on 2009-06-04
In my Ubuntu 8.10 system, when I start the PC, the following popup window is shown:

Enter password for default keyring to unlock

The application "Networkmanager Applet" (/usr/bin/nm-applet)
wants access to the default keyring, but is locked.

Does somebody know how to avoid this ?
Thanks
Luigi Fonti

---

### Post by blueridgedog on 2009-06-04
I have encountered this when a system is set to auto login.  When you elect to log in when the system starts, your keyring is unlocked, otherwise it asks you for a password when you attempt to use it the first time.

---

### Post by ActiveFrost on 2009-06-04
There should be an option to remember your password ( authentication checkbox at the bottom of that window ), and yes, it pops up only if your system is set to log in automatically.

---

