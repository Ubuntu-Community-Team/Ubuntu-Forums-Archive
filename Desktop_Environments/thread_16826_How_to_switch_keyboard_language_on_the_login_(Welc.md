---
title: "How to switch keyboard language on the login (Welcome) screen?"
date: 2005-02-24
forum: Desktop Environments
---

### Post by Sandu on 2005-02-24
How to switch keyboard language on the login screen? Can't log in because of russian language is default, but login is in latin symbols.  I tried "sudo dpkg-reconfigure locales" to install English as default -- this doesn't work!
What keyboard shortcut are to switch keyboard language in Ubuntu 4.10? Ctrl+Shift, Alt left, Alt+Alt etc. doesn't work?
Can anybody help? 3rd day after installing Ubuntu can not normally log in, only "recovery mode" :)

---

### Post by Sandu on 2005-02-25
[QUOTE=Sandu]I tried "sudo dpkg-reconfigure locales" to install English as default -- this doesn't work![/QUOTE]
Finally, I have edited in vi-redactor file "/etc/X11/XF86Config" and have replaced Option "XkbLayout" "ru" with "en". After reboot default language became English and I could login with latin username and passw.
But... Gnome desktop shows an error about wrong configuration of Xfree86 server, and now I can't switch to russian :)
Anybody knows what am I doing wrong?

---

