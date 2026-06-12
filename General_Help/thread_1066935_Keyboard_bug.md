---
title: "Keyboard bug?"
date: 2009-02-11
forum: General Help
---

### Post by Jac3510 on 2009-02-11
I've installed 8.10 on three different machines now, and on all three, I get the same bug. If I restart the computer and do not turn off the numlock key *during* the reboot, the keyboard will not respond at the login screen (I can't even turn off the numlock, meaning, the light on the keyboard won't even go out). This is especially odd given that the keyboard worked to select Ubuntu rather than XP earlier in the boot process. Anybody else ever have this problem, and if so, do you have a fix?

---

### Post by gettinoriginal on 2009-02-11
Alt F2 and type in the box: gconf-editor
desktop, gnome, peripherals, keyboard, "remember numlock state" , host, "numlock on"

---

