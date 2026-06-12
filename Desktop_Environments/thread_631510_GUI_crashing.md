---
title: "GUI crashing"
date: 2007-12-04
forum: Desktop Environments
---

### Post by johnnyw on 2007-12-04
My GUI started crashing after I upgraded from feisty to gusty. What can I do??


thanks

J

---

### Post by aamod on 2007-12-07
Copy the xorg.conf file from your old installation to new one. If you do not have the old file. rm the current xorg.conf and let it configure itself again.

---

### Post by erginemr on 2007-12-07
Hello,

Also you can try the following command from the console:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and restart your xserver (i.e. desktop) with Ctrl+Alt+BackSpace which supposedly will bring back your desktop.

---

