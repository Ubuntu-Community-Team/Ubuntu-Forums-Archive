---
title: "No swap memory being used"
date: 2006-05-09
forum: Desktop Environments
---

### Post by J77 on 2006-05-09
I'm having a major memory problem ](*,) 

Basically, the memory in my swap space isn't being used at all.

I have 4GB of RAM + 10GB set aside for swap.

It's on my desktop, so I'll have to type out what the following give:

**free**: Swap: 9767480 (total) 0 (used) 9767480 (free)

and

**/etc/fstab**: /dev/sda8 none swap sw 0 0

Also, **swapon -a** doesn't help ](*,) 

Can anyone help me, please :)

---

### Post by cgjones on 2006-05-09
If you have 4GB of RAM, you'll probably never need the swap. Plus, I wouldn't have a swap partition that big. It's overkill. If you have two hard drives, you could create two 2GB swap partitions, one on each drive. I've heard there is some sort of limit to the size of any single swap partiton, but I don't know if it's really an issue or not.

---

### Post by bluenova on 2006-05-09
4GB of RAM, lol, I don't think you're ever gonna need swap ;)

---

### Post by Sef on 2006-05-09
In general, if you have 1 GB of memory or more, you're not going to need swap, unless you are doing heavy gaming or digital video editing a lot.  Unless you are doing something like that, I'd get rid of the swap.

---

### Post by J77 on 2006-05-09
I need the swap for when I do hardcore sums...

:-k

---

### Post by cgjones on 2006-05-09
This is from the man page for mkswap.
> 
The maximum useful size of a swap area now depends on the architecture.
It  is  roughly  2GiB on i386, PPC, m68k, ARM, 1GiB on sparc, 512MiB on
mips, 128GiB on alpha and 3TiB on sparc64.


The newer kernels can support up to 32 swap partitions. I've read that the best way to go is to limit the size of each swap partition to 2GB, and spread them across the available hard drives. What do you have for hard drives?

---

### Post by J77 on 2006-05-09
I've got two SCSI drives.

---

### Post by cgjones on 2006-05-09
From the research I've done, there seem to be conflicting opinions as to how much swap you need (equal to RAM or twice RAM?). Given that you have 4GB of RAM, I would go equal to the RAM.

Since you have two drives, I would set it up (if you can) so that you have one 2GB swap on the first SCSI drive, and one 2GB swap on the second SCSI drive.

---

### Post by J77 on 2006-05-09
I'll give that a go, thanks.

Not straight away tho' - the computing gods aren't shining on me today (see recent thread)...

---

### Post by cgjones on 2006-05-09
I saw your new post. I have days like that, when anything I do seems to backfire. Good luck with everything.

---

### Post by Sef on 2006-05-09
> Not straight away tho' - the computing gods aren't shining on me today (see recent thread)...

Could you post a link to that thread, please.

---

