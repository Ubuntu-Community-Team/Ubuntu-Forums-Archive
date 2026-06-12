---
title: "Cache out of control?"
date: 2009-02-15
forum: General Help
---

### Post by NSAJEFF on 2009-02-15
I'm using 8.04(recently went 8.10-9.04-8.04) for several reasons. I'm noticing that regardless of distro my memory cache just blows up within 30 minutes. It jumps to about 80% with the other 20% in use by programs. Generally speaking, I understand this is not an issue. However, once the cache gets to this point I am not able to load online content(i.e., youtube/megavideo) without a fresh restart. This is far from ideal. Any suggestions are greatly appreciated.

---

### Post by NSAJEFF on 2009-02-15
Bump. Seems that with 8.04 it takes significantly longer to fill the cache. Is there some way to just flush it when I need to load online content?

---

### Post by jsowoc on 2009-03-17
I have the same problem. As I continue using the computer, I find (using "free -m") that about 2/3 of the memory is file cache, and that it put a significant portion of the programs I was running on the swap.

I recall there being an option somewhere (maybe when compiling the kernel?) to specify what percentage of the memory should be allocated to programs. Does anyone know where to set this? If it is in the kernel, any suggested references for how to recompile the official Ubuntu kernel changing only the one parameter?

In my case, I don't want to overload the SSD with swap writes, and writes to SSD are 10x slower than reads, so I'd much rather re-read 100 MB of files than have to write 10 MB of programs to swap.

My configuration:
Asus EEE PC 701 (512 MB of memory, 256 MB swap on sda2)
Ubuntu 8.04.2 LTS (32-bit), kernel 2.6.24-23-generic

---

### Post by sdennie on 2009-03-18
This is almost certainly not a cache related problem.  The cache is, in almost all cases, something that makes your computer run much, much faster.  The purpose of the cache is literally to prevent reading from the disk (which is orders of magnitude slower than reading from RAM).  If for some reason, your machine is running slow, I would find it hard to believe that it's related to the disk cache.

---

