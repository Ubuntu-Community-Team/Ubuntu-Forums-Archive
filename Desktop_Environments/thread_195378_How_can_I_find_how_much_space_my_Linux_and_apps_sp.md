---
title: "How can I find how much space my Linux and apps space"
date: 2006-06-12
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-06-12
Hi All,

A newbee question.

How can I find space occupied by OS and apps in all together and seperatly.

Regards,

Swaroop Kunduru.

---

### Post by nanotube on 2006-06-12
[QUOTE=SwaroopKunduru]Hi All,

A newbee question.

How can I find space occupied by OS and apps in all together and seperatly.

Regards,

Swaroop Kunduru.[/QUOTE]
use command "df" to see filesystem-wide listings, or command "du -sk" to see per-directory listings. so, eg, you can do```

du -sk /home/yourusername
``` to see how much space your stuff takes up. ```
sudo du -sk /usr
``` for everything in /usr (add sudo since your user may not have perms to read everything in a system dir)

---

### Post by Anduu on 2006-06-12
[QUOTE=nanotube]use command "df" to see filesystem-wide listings, or command "du -sk" to see per-directory listings. so, eg, you can do```

du -sk /home/yourusername
``` to see how much space your stuff takes up. ```
sudo du -sk /usr
``` for everything in /usr (add sudo since your user may not have perms to read everything in a system dir)[/QUOTE]

Somewhere I saw this command:

```
cd /; sudo du -h --max-depth=1
```

It gives quite a detailed per directory listing.

---

### Post by steveneddy on 2006-06-13
OK - but what about opening up your "Home" folder & look in the bottom left corner of the box. It should show free space. Just do the math. A 40 gig HD with 19.7 gig used, you have almost half a HD left. 

But the other stiff is cool, too.

:)

---

