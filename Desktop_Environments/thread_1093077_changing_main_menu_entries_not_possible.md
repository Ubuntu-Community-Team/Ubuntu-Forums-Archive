---
title: "changing main menu entries not possible"
date: 2009-03-11
forum: Desktop Environments
---

### Post by the666pack on 2009-03-11
hallo,

i run intrepid and i wanted to change the entries in the gnome main menu. however, after right click on the menu and "Edit Menus" nothing happens.

the same with the other way in the menu System > Settings > Main Menu

can someone tell me what might be the problem?

or maybe someone can give a hint in which file i should look for logs.

is there a command-line version of this edit-menu comand?

thanks for helping,

j

---

### Post by kellemes on 2009-03-11
Not sure what's going on here..
I do know you get a fine menu-editor with alacarte.
```
sudo apt-get install alacarte
```

---

### Post by the666pack on 2009-03-11
thanks a lot for helping.

with the help of the error-output of the alacarte program on the commandline i figured out what was the problem:

strangely the menu directory (~/.config/menus) had owner and group set to root. clearly as an unprivileged user i was not able to change the entries.

:guitar:

---

### Post by kellemes on 2009-03-12
> **the666pack said:**
> thanks a lot for helping.

Thanks, great to here I can actually help sometimes, eventhough I don't even use Ubuntu or Gnome ;-)

---

### Post by barmaley on 2009-03-14
Thanks, kellemes.
I had the same problem (which is rather strange after a fresh install), and your hint helped. Permissions of ./config folder were set ro root.
I appreciate your help.

---

