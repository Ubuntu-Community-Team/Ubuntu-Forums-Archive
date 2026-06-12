---
title: "&quot;Log out&quot; keyboard shortcut not working"
date: 2007-02-20
forum: Desktop Environments
---

### Post by petehall on 2007-02-20
Recently, the "Log Out" keyboard shortcut (in System > Preferences > Keyboard Shortcuts) seems to have stopped working. I've tried assigning various keys to this operation, but none of them produce any results.

Is this a known issue?

Thanks

---

### Post by Jeremy23 on 2007-02-21
Interesting. It doesn't work for me either on Ubuntu 6.10 with latest updates.

---

### Post by chrisstankevitz on 2007-08-16
Me too.  What can we do as a workaround?

Which application does the "Gnome quit/logout/whatever" button execute?

Chris

---

### Post by glosman15 on 2007-08-16
Same here, hasn't worked since I set it up.

---

### Post by praet on 2007-08-16
You could try to reinstall gdm:
```
$ sudo apt-get remove --purge gdm
$ sudo apt-get install gdm
```

Also, as an alternative, try Ctrl+Alt+Backspace which should kill your session and reload gdm, leaving you at the login screen.

---

### Post by Instrodi on 2007-10-20
Thanks praet, it worked for me. I had the same problem.

---

