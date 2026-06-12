---
title: "My swap partition is not beeing used"
date: 2006-01-14
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-14
anyone who can help me with this?
Its mounted under fstab as 
/dev/hda4       none            swap    sw              0       0

but its not beeing used.
Swap 0mg used out of allot
mem 485 out of 758 used...
Thats not right

---

### Post by syklitengutt on 2006-01-14
take a look at this:
chris@chris:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           758        743         15          0         92        261
-/+ buffers/cache:        388        369
Swap:         6275          0       6275

---

### Post by oakz on 2006-01-14
With 768MB of RAM, its not that unusual that none of your swap is being used. Remember that swap space will only get used if you are running out of RAM...

from a terminal, try:

$ cat /proc/swaps

... This file lists all of the active swap partitions, if /dev/hda4 is listed, your system will use the swap when its needed.

---

### Post by syklitengutt on 2006-01-14
chris@chris:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       6425992 0       -1

so that means its in use but not used?

And I know.,... wth was I thinking about... 6 gig swap... lol...

---

### Post by oakz on 2006-01-14
Yeah, I think you're safe with 6gig :)

From "man proc":

```
/proc/swaps
              Swap areas in use.  See also swapon (8).
```

---

### Post by handy on 2006-01-14
A lot of users worry that they are using too much RAM!

They don't realise that it is literally hundreds of times faster than reading / writing to a hard disk drive.

It is still the cheapest way to speed up a computer, while ever you don't have enough RAM to prevent hdd swap file usage.

---

