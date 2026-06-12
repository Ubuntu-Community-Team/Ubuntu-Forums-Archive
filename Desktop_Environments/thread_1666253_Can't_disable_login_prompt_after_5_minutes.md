---
title: "Can't disable login prompt after 5 minutes"
date: 2011-01-13
forum: Desktop Environments
---

### Post by johncc on 2011-01-13
> **lungten said:**
> If its the screensaver locking you out after a while of inactivity, ```
System->Preferences->Screensave->Lock screen when screensaver is avtive
```

I am having a problem with this.  In System/Preferences/Screensaver the "lock screen" is indeed UNchecked, but I am getting the login screen after about 5 minutes of idle.  

It had been behaving properly before, but I had had to uninstall nvidia drivers which led down a path where I uninstalled and reinstalled xserver-xorg.  Now X is working but I can't get rid of the password prompt.  ?

I also did this:
```
ALT+F2
Open gconf-editor.
Go to /apps/gnome-power-manager/lock/
Uncheck "Suspend"

```

And after 5 minutes it still went back to the login screen.

This is in 10.10

Thank you,
John

---

