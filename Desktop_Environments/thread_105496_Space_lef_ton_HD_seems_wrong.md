---
title: "Space lef ton HD seems wrong"
date: 2005-12-18
forum: Desktop Environments
---

### Post by madjinx on 2005-12-18
i have a 300gig Maxtor 10, which is 275.1 formated.

So its now at 259.3gig full, and system monitor says i have 15.2 gigs to go before i run out. But when i use nautilus to navigate to the dir, its only showing 1.2 gig free. SO i cant copy anything large into it now.

I thought there might be some hidden files, but none i can find. I also thought system monitor might be reporting wrong, and when i select all the dir on that drive and see how much they take up, lo-and-beho its only 259.3.

Wheres my 15.2 gig free?

---

### Post by ranf on 2005-12-18
What do you get from df in a terminal?
```
df -Th
```

---

### Post by madjinx on 2005-12-18
[QUOTE=ranf]What do you get from df in a terminal?
```
df -Th
```[/QUOTE]

/dev/sdb1     ext2    276G  260G  1.3G 100% /media/storage

so why is system monitor and nautilus reporting wrong. When i right click for properties, its still showing my 15 gig free?

its saying 1.3 gig free, but only 260gig out of 276 used? wtf! lol that 16 gig free! not 1.3!

---

### Post by ranf on 2005-12-18
Sorry, I don't know how these programs do the math and where they get their numbers from.

---

