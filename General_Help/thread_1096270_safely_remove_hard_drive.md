---
title: "safely remove hard drive"
date: 2009-03-14
forum: General Help
---

### Post by Stjepan_esa on 2009-03-14
When I try to safely remove my usb external hard drive: (WD 250GB in Transcend enclosure) i get this:

```
stjepan@stjepan-laptop:~$ sudo sdparm --command=stop /dev/sdb
    /dev/sdb: ST925042  1AS   

```

What to do? It won't stop spinning...

---

### Post by taurus on 2009-03-14
Is there a filesystem on that, /dev/sdb1?

If you want to unmount it, can you just run

```
sudo umount /dev/sdb1
```

---

### Post by ubfu on 2010-01-31
What if I wanted to power down the hard disk so it stop spinning first ?
the  triggered "Safely Remove Drive" works well on 9.10 but I wanted it for 8.04
Any command ?

---

