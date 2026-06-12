---
title: "deluge doesnt work in gnome, but does it unity"
date: 2017-05-18
forum: Desktop Environments
---

### Post by micahpage on 2017-05-18
I installed gnome and switched desktops. However deluge will not run when gnome is hte desktop. i purge, autoremoved, and reintalled deuge, but i still get the same problem.

```
metulburr@ubuntu:~$ deluge
metulburr@ubuntu:~$
```

nothing happens.

---

### Post by Xian on 2017-05-18
Try starting the program with gksudo. Then stop the program and try again to startup as normal user.

$ gksudo deluge

Exit the program

$ deluge

Any change?

---

