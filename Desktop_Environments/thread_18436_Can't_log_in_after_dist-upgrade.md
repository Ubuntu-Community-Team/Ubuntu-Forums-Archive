---
title: "Can't log in after dist-upgrade"
date: 2005-03-06
forum: Desktop Environments
---

### Post by sas13 on 2005-03-06
did a dist-upgrade today.
problem is this:
the upgrade included something to do with locales. I live in Israel and had hebrew language support, but my default language was English.

anyway, since the upgrade after a boot when I get to the login screen anything I type is in hebrew, so I can't log in - username and password are in english. (changing language from the login screen menu doesn't help)

I can get to a text console (ctrl-alt-F1) which will let me login and use my (english) keyboard, but I guess I don't know what to do from there (noob)

by the way I'm using Hoary.


thanks for any help!

---

### Post by Mlehliw on 2005-03-06
After you login with the text console can you use ctrl-alt-F7 to get back into X.

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Mlehliw]After you login with the text console can you use ctrl-alt-F7 to get back into X.[/QUOTE]


or command:

startx


after you login

---

### Post by sas13 on 2005-03-07
thanks for the replies, but they don't solve my problem.

yes, I know how to use ctrl-alt-F7 to get back to X, but I don't know how to solve my problem first - once I return to X it still asks me to log in, and it's still in hebrew.

what I was hoping for was instructions on how to reset the keyboard mapping or locale (I'm not sure which one would solve my problem) from the text terminal, so I can make the problem go away.

---

### Post by sas13 on 2005-03-07
fixed it:

edited xorg.conf       ($ sudo nano /etc/X11/xorg.conf)
changed value of "xkblayout"    from "il"  to "us"

---

