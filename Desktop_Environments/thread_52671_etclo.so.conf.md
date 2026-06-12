---
title: "/etc/lo.so.conf"
date: 2005-07-28
forum: Desktop Environments
---

### Post by simple on 2005-07-28
i accidentally overwrote the original content of this file as root, anybody mind pasting me what theirs says? something like /usr/lib/x or /usr/x/etc.. i can't remember, but since i did, i can't open anything.. luckily i had firefox open  :-|

---

### Post by jcohen on 2005-07-28
I've already helped simple with this problem on IRC but I figured I would paste the answer anyways. the filename is actually /etc/ld.so.conf

Edit the file by typing "sudo gedit /etc/ld.so.conf" in a terminal

/usr/X11R6/lib


After editing the file type "sudo ldconfig" in a terminal.

---

