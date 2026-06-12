---
title: "Help booting Windows XP from a previously Ubuntu - only system"
date: 2008-12-18
forum: General Help
---

### Post by whosmatt on 2008-12-18
I added a second hard drive to my system, disconnected the first drive (ubuntu) and installed windows.  Now I want to set up GRUB so that I can boot windows or Ubuntu.  So far no luck.  I can boot windows if I tell the bios to boot from the windows drive but GRUB will not boot it.

I'm sure this is something simple, but I'm not really finding the recipe I need. I added this to my menu.lst :

```
title XP
root (hd1,0)
chainloader +1
savedefault

```

and this to my device.map

```
(hd1)	/dev/sdb

```

but no luck so far.  i know this has to be simple.

-m

edit:

i also tried rootnoverify (hd1,0) to no avail.  I get "Starting up ..." and then a blinking cursor.

---

### Post by caljohnsmith on 2008-12-18
How about trying instead:
```
title XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
```

---

### Post by whosmatt on 2008-12-18
> **caljohnsmith said:**
> How about trying instead:
```
title XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
```


Thank you.  Works like a charm.

Can you explain what the "map" commands do?  Or should I just RTFM :P

---

### Post by lovelyvik293 on 2008-12-18
The "map" is used when you have two hard drives and the grub is installed in other then your windows HDD.

---

