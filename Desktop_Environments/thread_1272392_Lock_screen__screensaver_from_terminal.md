---
title: "Lock screen / screensaver from terminal"
date: 2009-09-22
forum: Desktop Environments
---

### Post by gspr on 2009-09-22
Hi. Is there a way to start the KDE screensaver / screen lock from a terminal? I run Xmonad as my WM, but KDM as my login manager. I'm able to start a second user session using "kdmctl reserve", but "kdmctl lock" does nothing. I'd like to be able to lock the screen, and then optionally launch a second session (as you can when locking the screen in KDE).

---

### Post by Lars Noodén on 2009-09-23
Do you mean this one  ?
```
/usr/lib/kde4/libexec/kscreenlocker
```

---

### Post by gspr on 2009-09-23
Ah, thanks. It seems only to be present in Karmic, though. But I guess I can wait, if it does the trick (have you tried?).

---

