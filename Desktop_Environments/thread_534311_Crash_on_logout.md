---
title: "Crash on logout"
date: 2007-08-25
forum: Desktop Environments
---

### Post by banko on 2007-08-25
Hi all

-->Fresh install of Feisty
-->Fetch and install all updates
-->Install beryl using ATI
-->Everything successful :-)

Can't logout anymore :-( Black screen and crash.  I have redone this three times.  Always works before installing Beryl, but the minute i follow the documentation for installing beryl, logout becomes impossible.

Any suggestions.  If you need any other information, please just let me know.

---

### Post by InGunsWeTrust on 2007-08-26
Well it is clear that the problem is in beryl. so try this:

```
killall beryl
beryl
```

This way you can get console output for beryl. Attempt to log out and see if there are any error messages in the console as you attempt to log out. If so post what the error messages say

---

### Post by banko on 2007-08-28
Hi all.

The problem is fixed.. turns out this is a double bug, and neither one has anything to do with Beryl!!!
To all you ATI users out there that want to use the restricted driver, it turns out that gdm (the login manager) has a bug. you need to:

sudo nano /etc/X11/gdm/gdm.conf
[Replace: AlwaysRestartServer=false With: AlwaysRestartServer=true]

A second word of warning.... this driver does not work well with any aspect of the shell.... try using any shell shortcuts such as switching to a new tty 1 through 6.  In other words press Ctrl + Alt + # where # is a number between 1 and 6.  Ctrl + Alt + 7 gets you back to tty 7 (X Server)

Oh well.... use restricted only if you want beryl guys otherwise stick with the default ati driver, as it intigrates and works well with everything but 3D :(

---

