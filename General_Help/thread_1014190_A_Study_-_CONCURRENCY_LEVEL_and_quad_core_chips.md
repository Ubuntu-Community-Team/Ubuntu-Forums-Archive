---
title: "A Study - CONCURRENCY_LEVEL and quad core chips"
date: 2008-12-17
forum: General Help
---

### Post by graysky on 2008-12-17
I have read conflicting info about what number to use when setting the CONCURRENCY_LEVEL variable prior to compiling a kernel.  Some guides teach to use 1+ the number of cores (5 in the case of a quad and 3 in the case of a dual) while others teach to use the number of cores (4 in the case of a quad and 2 in the case of a dual).

You can search these forums for guides on compiling it.  [Here](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html) is my favorite one.

I did a few compiles of the Lenny 2.26.6-1-amd64 kernel (just copied the /boot/config-2.6.26-1-amd64 to /usr/src/linux-source-2.6.26/.config) using a value for X in the code below of 1, 3, 4, and 5:

```
# export CONCURRENCY_LEVEL=X
# fakeroot make-kpkg clean
# time fakeroot make-kpkg --append-to-version "-trash" --revision "1" --us --uc --initrd kernel_image kernel_headers
```

Here are the results:

**CONCURRENCY_LEVEL=1**
real	27m55.944s 
user	23m56.166s 
sys	3m42.652s

[color=purple]**CONCURRENCY_LEVEL=3**[/color]
real	11m20.945s
user	23m33.358s
sys	3m45.215s

**[color=darkblue]CONCURRENCY_LEVEL=4[/color]**
real	10m51.692s 
user	22m57.254s 
sys	3m42.559s 

[color=red]**CONCURRENCY_LEVEL=5[/color]**
real	12m28.570s 
user	23m10.479s 
sys	3m49.568s

Hardware specs: Xeon X3360 @ 8.5x400 = 3.40 GHz; 4 gigs of DDR2 @ 1,003 MHz

Just so you know, they don't scale in a linear fashion because of many factors including, I/O limitations, the fact that the whole process isn't CPU limited, not all cores get 100 % utilization, etc.  Another factor I wanted to share is that the entire compile isn't using all four cores.  For example, when making the debs, only one core is used.  When writing the modules, the HDD becomes the limiting factor, etc.

Based on this small data set, one should NOT use 1+number of cores with CONCURRENCY_LEVEL.  I'll also do a similar analysis using make -jx and post it when completed.

---

### Post by sarang on 2009-02-17
Interesting. On my Core 2 Duo Laptop that has a 
```

model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11

```
processor, CONCURRENCY_LEVEL=3 is faster.

---

### Post by sdennie on 2009-02-17
> **graysky said:**
> Based on this small data set, one should NOT use 1+number of cores with CONCURRENCY_LEVEL.  I'll also do a similar analysis using make -jx and post it when completed.

These are really interesting numbers but I don't think you can conclude that.  What I see is, "For my setup, building a kernel with make-kpkg doesn't scale beyond CONCURRENCY_LEVEL=3" (the difference between 3 and 4 can be chalked up to noise).  But, that's not the whole story either I don't think.  I've recently started building stripped down kernels (as opposed to the full universe of modules you used in the test) and in that case, it doesn't even scale linearly to C_L=2 because the serialized parts of the build are taking larger and larger percentages of the build time (realtime).

I think CONCURRENCY_LEVEL is going to be very machine specific and also configuration specific.  People advocate the CPUS+1 maybe out of tradition when it was realistically feasible that computation and I/O could overlap because it took the compiler a while to chew on the source files.  CPUs have gotten faster since then but disks haven't kept pace so, that advice may not be relevant because the compiler can churn through source code faster than the disk can feed the compilation threads (which is why you aren't seeing scaling beyond 3 and probably why you are seeing a slowdown at 5).

If you want, I can kick off a bunch of builds on a Core 2 Duo 2.5Ghz (T9300) with a 7200rpm disk and 4G of RAM to add to your data points.  I'll happily supply full modular build numbers and stripped down module numbers at CONCURRENCY_LEVEL=1/2/3.

(On another note, I always build my kernels with INSTALL_MOD_STRIP=1.  It's been many years since I've built a kernel without that but, if I remember correctly, it makes the kernel package orders of magnitude smaller.  That could potentially reduce the amount of time you spend in serialized parts of the build).

---

