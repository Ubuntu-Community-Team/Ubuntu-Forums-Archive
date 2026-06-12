---
title: "Help Creating Desktop Shortcut Please."
date: 2009-02-26
forum: General Help
---

### Post by Agent Smith on 2009-02-26
Hi, I have just installed Open Office 3 to replace my 2.4 version. Everything went fine and it all works so i removed 2.4.
I would like to know how to get shortcuts for the new version on to the desktop.
When i drag them from the menu in applications, they appear on the desktop but they have a padlock on them and i cant rename them as it says i dont have permission. Apart from that they work fine.
I am using Ubuntu 8.04.
Thanks Jon.

---

### Post by taurus on 2009-02-26
It's probably because root is the owner of that file or shortcut.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by Agent Smith on 2009-02-26
It just so happened that someone posted a thread called padlocks at the same time as me. I have followed the instructions of that thread.
I typed gksudo nautilus in a terminal then changed the permissions of the executables. now i can rename them and there is no padlock. Thanks very much for your quick response though. Jon.

---

