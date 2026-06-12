---
title: "hibernate problem"
date: 2009-03-29
forum: General Help
---

### Post by ice_zoldik on 2009-03-29
hi all, im new in linux, especially ubuntu..
im using ubuntu 8.10
its about a week im using ubuntu..
and this is my first post hahahaha :lolflag:

i tried to hibernate and i've got 
**PM: not enough swap memory**

here my free -m

```
             total       used       free     shared    buffers     cached
Mem:          2014        860       1153          0         30        320
-/+ buffers/cache:        510       1504
Swap:         5139          0       5139

```

and this is my swapon -s
```
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	515792	0	100
/dev/sda8                               partition	4747168	0	-1

```

when i 
swapoff /dev/ramzswa0

 i can hibenate but when reboot, nothing happen, no reume or waking up..
i've check again  swapon -s and /ramzswap0 appear again..

is it because of ramzswap0?

any advise?

(forgive me if my english is bad, ](*,) :lolflag:)

---

### Post by ice_zoldik on 2009-03-29
help

---

### Post by ice_zoldik on 2009-03-31
anyone?

---

### Post by 3Miro on 2009-03-31
To hibernate you need to have enough swap enabled. Turning swap off would disable the hibernation.

When you get the hibernation message, is the swap on or off?

---

### Post by ice_zoldik on 2009-03-31
the swap is on, my swap partition is more than 4G, but my ubuntu still can't hibernate

---

