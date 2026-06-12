---
title: "User cannot log in"
date: 2007-08-04
forum: Dell  Ubuntu Support
---

### Post by DrIdiot on 2007-08-04
Hi,

I cannot log into X with a user.  I can log in using the Failsafe Terminal session and by using su harrison (username is harrison) in the terminal from another user.  This problem came up after I modified the default session for that user (I think).  I added "compiz --replace" and "screenlets-tray" to the default session.  Screenlets is now uninstalled from the system.  However, I still can't log in.  I've also noticed that logging in is significantly slower for the other user (compared to when I first used the OS).  If there's any logs that may help solve the poroblem, please tell me - I do not know where things are.

Also, I do not get any errors.  All that happens is it locks up.  Ctrl+Alt+Backspace does nothing so I have to do a hard reset.  The last line of .xsession-errors is:
(gnome-panel:5770): Wcnk-WARNING **: Unhandled action type (nil)

Thanks,
-Harrison

---

### Post by DrIdiot on 2007-08-05
Hmm, I fixed it.  I went into .gconf and deleted all the extra panel applets I added.

---

