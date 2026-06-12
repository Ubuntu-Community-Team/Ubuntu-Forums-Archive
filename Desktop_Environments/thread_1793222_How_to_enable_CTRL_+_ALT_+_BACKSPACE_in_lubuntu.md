---
title: "How to enable CTRL + ALT + BACKSPACE in lubuntu?"
date: 2011-06-29
forum: Desktop Environments
---

### Post by Bazon on 2011-06-29
short:
CTRL + ALT + BACKSPACE does nothing for me in lubuntu. How can I enable it to kill x?

long:
Although otherways very happy with lubuntu, recently my lxde panel froze and there was nothing I could do on anymore. So I'd like to use CTRL + ALT + BACKSPACE, but nothing happened. So what could I have done instead of rebooting?

---

### Post by mikewhatever on 2011-06-29
Really, there were several things you could have done.

1. ctrl-alt-f1, login, then **sudo service gdm restart**.

2. [Reboot gracefully]("http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/").

To enable ctrl-alt-backspace, open Keyboard, Layouts tab, Options, Key sequence to kill X.

---

### Post by Bazon on 2011-06-29
> **mikewhatever said:**
> 
1. ctrl-alt-f1, login, then **sudo service gdm restart**.
thanks!
> **mikewhatever said:**
> 
To enable ctrl-alt-backspace, open Keyboard, Layouts tab, Options, Key sequence to kill X.
No, that's not in **l**ubuntu: in lxkeymap, there is no "options".

---

### Post by mikewhatever on 2011-06-29
Of cause it isn't, silly me, Lubuntu. There used to be a package, dontzap, in the repositories that provided the option, but I don't see it now. An alternative would be to edit /etc/X11/xorg.conf and add the following:
```

Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection


```

---

### Post by Peadogie on 2011-06-29
Lubuntu does not uses GDM it uses LXDM.

Open /etc/xdg/lxsession/lubuntu/autostart as root and add:

@setxkbmap -option terminate:ctrl_alt_bksp

Log out . Your set.

---

### Post by Dave_L on 2011-06-29
Alt+Sysreq+k will kill X in Ubuntu.  I don't know if it works in Lubuntu.

---

### Post by ajgreeny on 2011-06-30
> **Dave_L said:**
> Alt+Sysreq+k will kill X in Ubuntu.  I don't know if it works in Lubuntu.
It surely does!

---

### Post by Bazon on 2011-06-30
Thanks, it does and that's all I need! :-)
(Sometimes it has to go fast...)

---

