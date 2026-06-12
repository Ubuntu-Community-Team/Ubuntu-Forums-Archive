---
title: "Onscreen keyboard appears at unlock screen"
date: 2012-03-15
forum: Desktop Environments
---

### Post by roger_1960 on 2012-03-15
Hi

A few days ago, out of curiosity, at boot up login I enabled the onscreen keyboard using the top panel control - worked fine - and disabled it again while still in the login screen - it went away.  I logged in and carried on as normal.  When I next had to enter my password to unlock the screen (after timeout) the onscreen keyboard appeared below the password window. It goes away again once the password is entered and the screen unlocks so does not affect use of the PC.  I had been unable to find how to stop this behaviour which persists at screen unlock (not at login)- not really a serious issue, but does anyone know where the setting is for this - happy to use CLI if needed.

Ubuntu 11.10 32 bit Unity.

---

### Post by rtg on 2012-04-21
This fixed it for me, I guess disabling the screen keyboard does not take into consideration the screensaver setting.
```
gsettings set org.gnome.desktop.screensaver embedded-keyboard-enabled false
```

---

### Post by roger_1960 on 2012-05-21
Hi

Just saw your post - many thanks that worked.

---

