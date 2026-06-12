---
title: "Preventing locking on XScreenSaver in Xubuntu?"
date: 2011-10-24
forum: Desktop Environments
---

### Post by paulehoffman on 2011-10-24
In Xubuntu 11.10, the XScreenSaver 5.14 seems to always require entering my password after restoring from Suspend. Is there a way to prevent this? FWIW, in the screen saver settings, I already have "Lock Screen After" unchecked.

---

### Post by Rodney9 on 2011-10-24
> **paulehoffman said:**
> In Xubuntu 11.10, the XScreenSaver 5.14 seems to always require entering my password after restoring from Suspend. Is there a way to prevent this? FWIW, in the screen saver settings, I already have "Lock Screen After" unchecked.

Have you got "Lock Screen After" unchecked in 'Settings'  'Power Manager' -

---

### Post by paulehoffman on 2011-10-24
I didn't know about that one, but it doesn't fix the problem. That is, I turn off that option, reboot, check that the option is still off, suspend, and wake up: I am still prompted for the password.

---

### Post by Rodney9 on 2011-10-25
Thanks to Nama at [http://www.groupofnowhere.com/2011/10/19/xubuntu-11-10-oneiric-ocelot/](http://www.groupofnowhere.com/2011/10/19/xubuntu-11-10-oneiric-ocelot/)

> to solve the Xubuntu / lightdm auto login issue.  It’s just a matter of editing:

/etc/lightdm/lightdm.conf

to look like this:

```
[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=(your freaking username goes here)
autologin-user-timeout=0
```

---

### Post by paulehoffman on 2011-10-25
Thanks, but that didn't help either because the file already had those settings. You didn't mention was the setting for "autologin-guest" in that file, but trying both "true" and "false" came up with the same result: it still wants my password.

Other guesses are still desired. :-)

---

