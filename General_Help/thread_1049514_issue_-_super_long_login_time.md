---
title: "issue - super long login time"
date: 2009-01-24
forum: General Help
---

### Post by bishman on 2009-01-24
Hi all

Using Ubuntu 8.10, on Compaq EVO N610c laptop.

Having a problem with logging into ubuntu - it takes about 5 minutes! It started happening around the same time I tried to get 1394 dv input working by changing the permissions of /dev/raw1394, but this could be completely unrelated.

What I DO know is that it hangs on GDM - I have a different color background between gdm and gnome desktop.

So far I have tried creating a new user for me but it still does the same thing.

Any ideas? Thanks

---

### Post by bishman on 2009-01-24
bump

---

### Post by Procuro on 2009-01-24
Hi, I would try typing 'gnome-session-properties' in the terminal and uncheck any startup programs that you don't need. Hopefully it's one obvious program that's the issue

---

