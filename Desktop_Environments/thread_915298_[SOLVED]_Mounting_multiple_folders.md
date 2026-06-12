---
title: "[SOLVED] Mounting multiple folders?"
date: 2008-09-09
forum: Desktop Environments
---

### Post by ARhere on 2008-09-09
I have a USB hard drive with all of my work, music and other data I use a lot.  

I am going to mount the drive */dev* under ~/Documents in FSTAB but I also want ~/Music to point to */dev/Music*.

Is this possible?

-AR

---

### Post by ARhere on 2008-09-09
I think I am blacklisted, lack of responses. :confused:

*"No body loves me, everybody hates me, think I'll go eat worms...."*

-AR

---

### Post by sisco311 on 2008-09-10
try to add something like this:
> */mount/point*/Music /home/*username/*Music auto bindto the fstab

assuming that the partition is mounted in */mount/point*/ and
the Music directory exist in your home folder.

---

### Post by ARhere on 2008-09-10
that did it!

I was just missing the "bind" option.

Thank you.
-AR

---

