---
title: "Nautilus - segmentation fault (core dumped)"
date: 2006-11-21
forum: Desktop Environments
---

### Post by Vion on 2006-11-21
After a forced fsck, I cannot open any nautilus window (home directory etc.) and all desktop icons including wallpaper disappeared. When I try to run nautilus from terminal, I get the "Segmentation fault (core dumped)" message. Neither restart nor apt-get update helps. What shall I do?

---

### Post by rabicula on 2008-03-01
Same thing for me after last update.
Works fine after downgrading nautilus from 1:2.20.0-0ubuntu7.1 to 1:2.20.0-0ubuntu7.

---

### Post by DAEDALUS_ on 2008-04-02
I got the same problem
the cause is in -> libnautilus-extension1 1:2.21.6-0ubuntu1

---

