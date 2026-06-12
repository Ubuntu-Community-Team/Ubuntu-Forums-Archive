---
title: "Ubuntu and Firefox JavaScript/Flash Performance."
date: 2009-02-19
forum: General Help
---

### Post by JTLJudoMan on 2009-02-19
I recently read an article about how firefox in wine performs better than firefox in native Ubuntu so I decided to run the test for myself.
I also use a sun xVM VirtualBox running windows xp.

The first thing I wanted to test was flash performance. So I used Googled flash benchmarks and decided to go with POWERBENCH.  Here are the results.

Native Ubuntu with flash 10.0 - 1780
Ubuntu + Wine + flash 10.0.12.36 - 2101
Sun Virtual Box + Windows XP + Flash 10.0.12.36- 2788

Yeah... A virtual machine running inside of Ubuntu 8.10 performs the best out of the three options.

I used the google v8 benchmarking program and found the following results.

Native Ubuntu with flash 10.0 - 169
Ubuntu + Wine + flash 10.0.12.36 - 193
Sun Virtual Box + Windows XP + Flash 10.0.12.36- 176

Now we have a new leader Wine!  Still... Ubuntu's Firefox natively performs the poorest out of the three with a virtualized version still performing faster.

Why exactly is this?  Are the coders who were put in charge of Firefox on Linux so incompetent that it is consistently behind?  Its slower than a Virtual Box by 1.566x at flash code and its slower than even the wine counterpart of itself by a factor of 1.142x at JavaScript.

As a bit of background information here are a few of the specifications for my computer.

Ubuntu 8.10 (intrepid)
Kernel Linux 2.6.27-11-generic

2xIntel(R) Xeon(R) Cpu - 5140 @ 2.33Ghz
(Dual Dual Core)
3.2GB FB DDR2 memory
Raid 5 Array utilizing an array controller to prevent most of the load on the CPU.

Honestly I would like to know what's going on.  I always hear about how Linux is so much better than Windows at everything.  Clearly in Firefox that is not the case.

Shouldn't the streamlined architecture of Linux excel in web browsing?

---

### Post by JTLJudoMan on 2009-02-25
No replies from anyone as to why this is the case?

Wild speculation is totally acceptable.

---

### Post by shyft on 2009-03-11
cause linux and most OSS ******* sucks...

but, then again, that's why i use it.

---

