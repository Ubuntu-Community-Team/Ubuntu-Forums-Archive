---
title: "Contiguous RAM"
date: 2007-09-17
forum: Desktop Environments
---

### Post by reader4 on 2007-09-17
I run a lot of computer simulation software on my system and have a question about how RAM is allocated and managed in Linux.  The system is actually 32-bit CentOS 4.4 (not by choice) with 4GB of RAM.  The simulations I run allocate memory as needed because the solvers are iterative.  This is not normally and issuse, but occasionally I run into a problem that the solver has run out of memory.  When watching "top", memory use never exceeds 1GB for that simulation, but the problem seems to be that it cannot find a 1GB block of *contiguous* RAM.  If I restart the system, everything runs fine and there are no memory allocation problems.

I don't know much about how Linux manages memory, but was under the impression that the OS will use memory as needed and decrease the amount it uses if required.  When the system is freshly booted, it never uses more than 500MB of RAM.  After a simulation has run and the program exited, however, it shows 3GB+ as "used" (again, with top).  This will gradually decrease, but never seems to return to the original baseline.

So, I guess I have a few questions... first, how does Linux handle memory, especially after an application shuts down?  Next, is there a way to sort of "defrag" the RAM so that I can open large contiguous blocks without restarting?  Finally, is there a way to limit the amount of RAM the OS and critical processes use - almost like partitioning the RAM space so that large blocks stay clear?

Thanks for your help!

---

### Post by Wolki on 2007-09-17
Linux will use unused memory to cache data from the filesystem for faster access. The command 'free' will show you both the raw memory use and the memory use excluding bufers and cache.

Unfortunately I can't really help you with your other problems. :-/

---

