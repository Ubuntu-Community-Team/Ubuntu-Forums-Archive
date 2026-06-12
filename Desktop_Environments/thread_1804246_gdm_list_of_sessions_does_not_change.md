---
title: "gdm list of sessions does not change"
date: 2011-07-14
forum: Desktop Environments
---

### Post by andreas.kotowicz on 2011-07-14
Going through the docs, I assume that any .desktop file that is found inside 

```
/usr/share/xsessions
```

will show up in the GDM login screen as a valid session. However, this is not the case. E.g., I have a stumpwm.desktop file with the following content:

```
[Desktop Entry]
Encoding=UTF-8
Name=StumpWM
Comment=This session logs you into StumpWM (a minimalistic window manager)
Exec=/usr/local/bin/stumpwm
TryExec=/usr/local/bin/stumpwm
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```

but I do not see an entry for it in the list of sessions. The same is true if I go to "System -> Administration -> Login Screen" - I don't see all sessions in the list for the default sessions.

what's going on here? Do I need to tell GDM to go through this list again? I've tried restarting GDM but no success. This is ubuntu 11.04 btw.

---

### Post by Krytarik on 2011-07-14
1. Make sure the permissions of those file are set to 644.

2. Try renaming the file to "stumpwm.desktop", for example, which I would have chosen in the first place anyway, and not modifying the "xterm.desktop".

Greetings.

---

### Post by andreas.kotowicz on 2011-07-15
> **Krytarik said:**
> 1. Make sure the permissions of those file are set to 644.


```

$ ls -la /usr/share/xsessions/stumpwm.desktop
-rw-r--r-- 1 root root 229 2011-07-14 18:52 /usr/share/xsessions/stumpwm.desktop



```

> **Krytarik said:**
> 
2. Try renaming the file to "stumpwm.desktop", for example, which I would have chosen in the first place anyway, and not modifying the "xterm.desktop".

Greetings.

I've done that but this doesn't make a difference.

---

### Post by andreas.kotowicz on 2011-07-15
I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/810894]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/810894")

---

