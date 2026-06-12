---
title: "HT Technology"
date: 2006-08-11
forum: Desktop Environments
---

### Post by alecjw on 2006-08-11
I have a dual core Intel P4 3.2GHz with HT. Is Ubuntu compatible with HT?

---

### Post by kaffelars on 2006-08-11
Indeed :D 
However, a HT-capable CPU is handled like two CPUs, which means you need a SMP-capable kernel to get the most out of it.

What you need to do is install the package called linux-image-something-**i686**.

By default, Ubuntu installs the i386-kernel, which works fine, but it's of course better to install a kernel optimized to your CPU.

Good luck :)

---

### Post by alecjw on 2006-08-11
It's only a 32Bit processor, so i shouod only need the x86 kernel, I think.

---

### Post by robinl on 2006-08-11
get the 686 smp kernel if you want the full power of your processor, but the default one works

---

### Post by kaffelars on 2006-08-11
Yes, it's 32-bit but i386 and i686 are both 32-bit. The practical difference is that i686 is for newer CPUs (I've read that this is from Pentium Pro and up).

Some of the newer P4's are EM64T-compatible however, which means that the can run 64-bit OS's as well. I think the BIOS can tell you this. (I have a Pentium D, and can enable and disable EM64T in BIOS).

---

### Post by meindian523 on 2007-06-19
I have Pentium D 2.80 GHz processor,how can we find out whether the kernel installed is 686 SMP or otherwise?

---

