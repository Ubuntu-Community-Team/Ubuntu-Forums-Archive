---
title: "Change file permissions from a live cd"
date: 2009-03-20
forum: General Help
---

### Post by YorNamHere on 2009-03-20
I have a Asus EEE900 with eeebuntu 2.0 (Ubuntu 8.10) installed and somehow many of my files in my root folder have become unreadable, including the GRUB files (I now get error 17 when i boot).  When I boot from a live cd, I can see the files, but I can't open, copy or change the permissions on them.  I'm sure that there is a way to fix this through the command line, but I am not very fluent with it.

If anyone can tell me a way to change this through Nautilus or how to change it through the command line, I would be very grateful.

-YNH

---

### Post by taurus on 2009-03-20
Run nautilus with root privilege.

```
gksudo nautilus
```

---

