---
title: "32bit versions RAM support?"
date: 2009-04-18
forum: General Help
---

### Post by dhysk on 2009-04-18
I was wondering if 8.10 or 9.04 32 bit versions support more than the 3.2 GB or ram.  I'm currently running 8.04 and although I have 4.16(2x2GB XMS2) GB ram as shown in POST Ubuntu only shows 2.5 GB, although from what I understand It should show 3.2 GB.

What is the max amount of RAM the 32bit versions of 8.10 and 9.04 actually use?

---

### Post by kevstar31 on 2009-04-18
4GB is the limit.
[http://en.wikipedia.org/wiki/64-bit#Pros_and_cons]("http://en.wikipedia.org/wiki/64-bit#Pros_and_cons")
> Pros and cons

A common misconception is that 64-bit architectures are no better than 32-bit architectures unless the computer has more than 4 GB of memory. This is not entirely true:

    * Some operating systems reserve portions of process address space for OS use, effectively reducing the total address space available for mapping memory for user programs. For instance, Windows XP DLLs and userland OS components are mapped into each process's address space, leaving only 2 to 3.8 GB (depending on the settings) address space available, even if the computer has 4 GB of RAM. This restriction is not present in 64-bit operating systems. (This also applies to computers running Windows Vista with Service Pack 1 as it only shows the installed RAM not the usable.)

    * Memory-mapped files are becoming more difficult to implement in 32-bit architectures, especially due to the introduction of relatively cheap recordable DVD technology. A 4 GB file is no longer uncommon, and such large files cannot be memory mapped easily to 32-bit architectures; only a region of the file can be mapped into the address space, and to access such a file by memory mapping, those regions will have to be mapped into and out of the address space as needed. This is a problem, as memory mapping remains one of the most efficient disk-to-memory methods, when properly implemented by the OS.
    * Some programs such as data encryption software can benefit greatly from 64-bit registers (if the software is 64-bit compiled) and effectively execute 3 to 5 times faster on 64-bit than on 32-bit.

    * Some complex numerical analysis algorithms are limited in their precision by the errors that can creep in because not all floating point numbers can be accurately represented with a small number of bits. Creeping inaccuracies can lead to incorrect results, often leading to attempts to divide by zero, or to not identify two quantities as being identical for practical purposes. International Computers Limited added 128-bit support to the ICL 2900 Series in 1974 largely as a result of requests from the scientific community.

The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization. Maintaining a partial 32-bit model is one way to handle this and is in general reasonably effective. In fact, the highly performance-oriented z/OS operating system takes this approach currently, requiring program code to reside in any number of 32-bit address spaces while data objects can (optionally) reside in 64-bit regions.

Currently, most commercial x86 software is compiled into 32-bit code, not 64-bit code, so it does not take advantage of the larger 64-bit address space or wider 64-bit registers and data paths on x86 processors, or the additional registers in 64-bit mode. However, users of most RISC platforms, and users of free or open source operating systems (where the source code is available for recompiling with a 64-bit compiler) have been able to use exclusive 64-bit computing environments for years. Not all such applications require a large address space nor manipulate 64-bit data items, so they wouldn't benefit from the larger address space or wider registers and data paths. The main advantage to 64-bit versions of such applications is the ability to access more registers in the x86-64 architecture.

---

### Post by dhysk on 2009-04-18
Thank you, I understand that however I have an Intel core 2 duo and I believe it will work with PAE(Physical Address Extension).  It doesn't seem to be enabled in the kernel by default in 8.04.  PAE will allow 32 bit OS's to run up to 64 GB of ram.  I guess to simplify the question, do the later releases 8.10 & 9.04 32bit have this enabled by default?  I also am not sure what the down sides to using PAE is so if anyone has any inputs please feel free to reply.

I still don't understand why it only sees 2.5 GB right now instead of 3.2 - 3.5 that most people report.  If I take either stick out it will show the whole 2.046 GB.  I was thinking about moving to the 64 bit when 9.04 comes out next week however I'm not sure I want to deal with getting all my fav 32bit programs to work.  (ie.. X-Plane9 and True Combat:Elite)

---

### Post by kevstar31 on 2009-04-19
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/")

---

### Post by dhysk on 2009-04-19
Thank you, Thats actually the exact page I was looking at, I was just wondering if it was enabled on 9.04 and what this communaties inputs on PAE where.

---

### Post by Slim Odds on 2009-04-19
> **dhysk said:**
> ...  I also am not sure what the down sides to using PAE is so if anyone has any inputs please feel free to reply.

You do pay a slight performance hit for using PAE. Also, many people suggest using the server kernel because it has PAE enabled. But, it also has other configuration setting that make it less desirable for desktop GUI type system (longer timeslice, etc.).

I'd give the 64 bit a try.... you can always go back to 32 if it's too much trouble...

I'm personally loving the 64 bit version, but then again I have 8G of RAM.

---

