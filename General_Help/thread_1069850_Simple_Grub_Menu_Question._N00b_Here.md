---
title: "Simple Grub Menu Question. N00b Here"
date: 2009-02-14
forum: General Help
---

### Post by MikeonTV on 2009-02-14
I had a version of OSX86 on my computer for some time and I cracked open the HDD and partitioned some space for Ubuntu (8.10).

I did all this using GParted. Now as you can see in the image below (a screenshot of my partitions) I have the OSX86 partition before Ibex. 

I am in my boot grub menu.lst and want to write in the correct coordinates for that OSX86 partition to be an option when booting but I am unable to figure it out.

Mind taking a peek at the image below and letting me in on what to do?

Regards.
[IMG]http://i40.tinypic.com/102p5dj.png[/IMG]

---

### Post by MikeonTV on 2009-02-14
anyone around?

---

### Post by dcstar on 2009-02-14
> **MikeonTV said:**
> I had a version of OSX86 on my computer for some time and I cracked open the HDD and partitioned some space for Ubuntu (8.10).

I did all this using GParted. Now as you can see in the image below (a screenshot of my partitions) I have the OSX86 partition before Ibex. 

I am in my boot grub menu.lst and want to write in the correct coordinates for that OSX86 partition to be an option when booting but I am unable to figure it out.
......

Add this to the end of your menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		osx86
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by MikeonTV on 2009-02-15
Hi. Thanks for your swift response. Unfortunately adding that to my menu has given me a different error


```
Starting Up
H0000000
HFS+ Partition Error
```

Thanks for trying. :(

---

