---
title: "Can't Hibernate e1505"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cartisdm on 2008-06-11
First off, I'm sorry because I'm sure there are threads exactly like this one elsewhere but I was unable to get anything of usefulness.  I have a Inspiron e1505 using ATI graphics cards (restricted drivers).  Could someone point me in the direction of how to get my hibernate to work?  It's really annoying to constantly have to shutdown and log back in every time.

(I'm using Hardy)

---

### Post by fragos on 2008-06-12
Make sure you have more swap space than RAM. I have no experience with ATI other than to know Linux is better supported by Nvidia and Intel X3100.

---

### Post by cartisdm on 2008-06-12
> **fragos said:**
> Make sure you have more swap space than RAM. I have no experience with ATI other than to know Linux is better supported by Nvidia and Intel X3100.

Well I imagine that I only set up the minimum swap drive (or close to it) so it's probably only 512.  My ram is 2gb, how can I go about changing the size of the swap space?

---

### Post by fragos on 2008-06-12
Ideally you'd increase the size of the swap position. The exact how depends on what partitions you already have. If you have a default full disk install, you'll need to boot from a CD like the one you installed from. No partitions will be mounted and you'll have more freedom to change partion sizes. 1st I'd shrink your "/" partition by some even multiple over your RAM size. 2nd, delete the old swap and format the freed space as swap. /etc/fstab will need to change to reflect the partitioning but the partition editor may do that for you automatically.

---

