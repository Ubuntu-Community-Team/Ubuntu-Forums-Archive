---
title: "Adding more RAM prevents X working"
date: 2008-12-14
forum: General Help
---

### Post by dalis on 2008-12-14
I increased the RAM on  my laptop from 1G to 4G but now the desktop doesnt work anymore.( Ubuntu 8.10 - X64) - only the command line is available. (The desktop does appear but is full of random noise and entirely without meaning)
(PC is dual boot - and Windows reports 3.2G available).
I've tried adding MEM=3100M to the kernel line in GRUB without success. Also tried MEM=1000M - also to no effect.
thanks - dalis

---

### Post by comspy on 2008-12-14
Hi dalis,

If you take the 4GB out and put the original 1GB back in, does Ubuntu boot to the desktop? If not, have you tried running "startx" from the command line?

---

### Post by sedawk on 2008-12-14
What happens when starting from the LiveCD - same problem?

What happens if you run/boot memcheck from the LiveCD and let
it run for an hour (can it test the full 4 GB anyway?)?

---

### Post by linux_tech on 2008-12-14
Try booting from live cd and running memtest86 to see if it shows any memory errors

---

### Post by dalis on 2008-12-14
> **comspy said:**
> Hi dalis,

If you take the 4GB out and put the original 1GB back in, does Ubuntu boot to the desktop? If not, have you tried running "startx" from the command line?
When I replace one of the 2G memory banks with a 512M then X starts and works properly.

---

### Post by dalis on 2008-12-14
> **sedawk said:**
> What happens when starting from the LiveCD - same problem?

What happens if you run/boot memcheck from the LiveCD and let
it run for an hour (can it test the full 4 GB anyway?)?
I have a 'SysRestore CD' that I used to partition the disk - it's a live CD that uses an older version of linux than on my hard disk.

However, when I run startx from it I get the same problem (when there's 4G installed).

---

### Post by comspy on 2008-12-19
> **dalis said:**
> When I replace one of the 2G memory banks with a 512M then X starts and works properly.

Does it matter which 2GB stick you take out?

---

### Post by dcstar on 2008-12-20
> **dalis said:**
> When I replace one of the 2G memory banks with a 512M then X starts and works properly.

You may need to go into your BIOS and change the setting that maps the video card resources.

---

