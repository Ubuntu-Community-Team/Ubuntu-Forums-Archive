---
title: "Quake 4 Problems"
date: 2006-04-22
forum: Gaming &amp; Leisure
---

### Post by danakatheone on 2006-04-22
I just recently installed Quake 4 and I can't seem to make any changes to the directory ingame (I can't save games or settings). I tried chmod on some of the config files. It didn't work. Any ideas?

---

### Post by Thorin on 2006-04-23
Sounds to me like the folder you wrote to has your permissions blocked out. I imagine you used sudo to install, which put the files somewhere a regular user can't edit. Try running Quake 4 in sudo, might help.

---

### Post by minisori on 2006-04-23
Or just change the owner of those files/folder. From your home directory:

chown -R your_username:your_username .quake4

---

