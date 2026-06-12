---
title: "Reduce delay time when launching an application?"
date: 2009-03-15
forum: Desktop Environments
---

### Post by hongquan1987 on 2009-03-15
When launching an application, I always have to wait a while (especially long with Firefox) before it shows completely. What can I do in order not to wait any more?

---

### Post by inobe on 2009-03-15
my applications load instantly, i have 1 gig of ram and a dual core cpu.



it may just be low system resources

---

### Post by konqueror7 on 2009-03-15
```
sudo apt-get install preload
```

here for more [info]("http://ubuntuforums.org/showthread.php?t=189192") regarding performance and stuffs...

hope it helps...

---

### Post by lisati on 2009-03-15
What sort of RAM do you have on your system? On the laptop I normally use for Ubuntu, I have only 222Mb available RAM, and loading programs tends to make things sluggish. On my other laptop, which has 2Gb ram, starting programs was a breeze when I had Ubuntu on it.

---

### Post by hongquan1987 on 2009-03-15
> **inobe said:**
> my applications load instantly, i have 1 gig of ram and a dual core cpu.
it may just be low system resources

Is there no way but upgrading hardware? I think upgrading hardware must be latest choice.

When I upgrade RAM 512MB to 1.2GB, there's no clear change.

---

### Post by krismatth3 on 2009-03-15
> **hongquan1987 said:**
> When I upgrade RAM 512MB to 1.2GB, there's no clear change.

Is this a physical machine or a virtual machine? What type of storage is being used? What load is the system under (e.g. what else is going on?)

---

### Post by hongquan1987 on 2009-03-16
> **krism said:**
> Is this a physical machine or a virtual machine? What type of storage is being used? What load is the system under (e.g. what else is going on?)

Physical machine.
Your question is ambiguous. I used DDR-RAM, HDD's kind of IDE. Is that what you asked?

---

### Post by HavocXphere on 2009-03-16
Make sure that your hard drives are 7200rpm drives, not 5400. Make quite a difference.

With FF, its often the add-ons that load slowly. e.g. Ad block plus loads the block list, which is painfully slow.

---

