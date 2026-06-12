---
title: "[SOLVED] Need press key constantly to boot"
date: 2008-12-05
forum: General Help
---

### Post by rolodoom on 2008-12-05
When I boot ubuntu livecd 8.10 in my dv6721la, it freezes when booting. I need to press down a key and then it continues loading.

If I use acpi=off, there's no need to press key, but there's no battery support, I mean the battery doesn't charge.

If i use noacpi, the problems repeats, need to constantly press a key to load the system.

Any suggestion??

---

### Post by rolodoom on 2008-12-05
Well, I found the solution here:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=966313](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=966313)

I added  "hpet=disable"  to my boot line at menu.lst, and fixed the problem.

---

