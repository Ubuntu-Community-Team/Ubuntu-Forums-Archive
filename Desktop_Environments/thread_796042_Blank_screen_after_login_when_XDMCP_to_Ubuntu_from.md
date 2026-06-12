---
title: "Blank screen after login when XDMCP to Ubuntu from Windows Xming"
date: 2008-05-16
forum: Desktop Environments
---

### Post by sharkey77 on 2008-05-16
After logging into Ubuntu from XP nothing comes up.  All I get is the desktop screen.

I have:

Allowed ports TCP 6000, 16001 UPD 177

Disabled firewalls completely

Disabled ESD

Modified gdm.conf to include ```
KillInitClient=false
```

Disabled the clipboard

I know the login is successful (but I can't see any icons) because when I go to the local computer it states I am already logged in or vice versa.  If logged in via XDMCP already when I login locally I get an error message about ISD and port 5800.  I believe 5800 is used by VNC but I am not running that so it may be unrelated.

---

### Post by snelo on 2008-05-16
I'm having the same problem - I'm running Xming on a Vista box connecting to a Ubuntu box configured as an Edubuntu Classroom server

---

### Post by sharkey77 on 2008-05-21
**bump**

Thank you.

---

### Post by bmjbmj on 2008-11-12
I have the same configration as Selno (Xming on a Vista box connecting to a Ubuntu box configured as an Edubuntu Classroom server). And the same problem.

I can login from other ubuntu/kubuntu computers and from LTSP clients, but not from Xming 

If you wait long enought (3-20 minuts) you get an error msg. About "There was an error starting the GNOME Settings Daemon"

Ther is more information her:

[http://ubuntuforums.org/archive/index.php/t-325868.html](http://ubuntuforums.org/archive/index.php/t-325868.html)

Non of it worked for me.

---

