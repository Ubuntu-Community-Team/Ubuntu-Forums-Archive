---
title: "Ubuntu GUI not loading"
date: 2008-12-23
forum: Desktop Environments
---

### Post by imgod22222 on 2008-12-23
I can boot ubuntu fine. The login sound plays, then... the desktop is the equivalent of explorer.exe not running in windows. But also, keybindings wont work. For example, f12 wont open a terminal anymore.
This happened because I ran the update package manager.

Any ideas on how to get the UI to show again? I'm starting to prefer linux > windows, but only when linux behaves properly...

---

### Post by namdung on 2008-12-23
Reboot in Recovery Mode and fix the XOrg Server.

Check System-->Preferences-->Keyboard Shortcuts for keyboard bindings.

---

### Post by imgod22222 on 2008-12-23
What should I type in terminal though? I haven't tried recovery mode yet, but what should I do so in normal boot my bars + desktop items, etc show up?

---

### Post by namdung on 2008-12-24
While booting press ESC key to go to Recovery Mode. Here select option to fix the XOrg server. Usually this solution works.

---

### Post by imgod22222 on 2008-12-24
booted into recovery mode. did the dpkg to fix broken packages (maybe?) and I also clicked xfix(fix the x.org server) and to no avail.
I can drop to bash root prompt (something like that, I forgot already)

---

### Post by imgod22222 on 2008-12-28
*bump?*

---

### Post by pietjanjaap on 2008-12-28
Fix x again in recovery mode.

In textmode sudo dpkg-reconfigure xserver-xorg -phigh

---

### Post by imgod22222 on 2008-12-28
how many times should I do this?

and the bash shell thing says "sudo is not a recognized command"

---

### Post by imgod22222 on 2009-01-01
*bump again*

---

### Post by imgod22222 on 2009-01-05
*bump!*

---

