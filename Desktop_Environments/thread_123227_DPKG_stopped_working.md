---
title: "DPKG stopped working"
date: 2006-01-29
forum: Desktop Environments
---

### Post by ashrack on 2006-01-29
```
 sudo dpkg -i wrath.deb
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `),' must be followed by colon

```
I attach the 'available' file:

---

### Post by az on 2006-01-29
Try

sudo dpkg --clear-avail

and then apt-get update

---

