---
title: "HELP! Compiz wont let me log in"
date: 2008-09-16
forum: Desktop Environments
---

### Post by blazemore on 2008-09-16
KDE4

I changed the compositing to Compiz using the System Settings GUI.
Now when I login, I get the splashscreen, but then it goes black,  (just after when compiz should load)and I can only move my cursor around.
How can I change it back to Kwin (or whatever the default it called) using only the command line? Oh, and I have no Internet as well, so can't apt-get anything.

Cheers

---

### Post by Peter Frank on 2008-09-16
Try this. 1.Back up the .kde4 folder. "cp -r .kde4 .kde4backup"
2.remove .kde4 folder. "rm -rf .kde4", so the Compiz setting won't be loaded.
3.Login. (A fresh .kde4 folder will be created)

I admit that this is not an ideal solution as you discard all the previous desktop settings, but may be worth trying if you are desperate to bring up a desktop.

---

### Post by danns on 2008-10-24
You can turn compositing off by editing the file:  .kde/share/config/kwinrc and setting compositing to Enabled=false.  This way you can retain the rest of your settings.

---

