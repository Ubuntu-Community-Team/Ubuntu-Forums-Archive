---
title: "Supported chipset and cpu type"
date: 2006-07-05
forum: Desktop Environments
---

### Post by bosonflux on 2006-07-05
Is there a place where I can find detailed information on what chipsets and cpu types are fully supported by the 2.6.15 kernel, or any kernel for that matter? I am using an Intel i975 board with a Core Duo processor. The device manager properly shows two cpus, but both the Vendor and Device are listed as "unknown". The capabilities are listed as just "processor". I am currently using the 2.6.15-25-686-smp kernel version.
 
I have noticed in menuconfig that there is a selection for pentium m, which would be a closer arch match than pentium 4. Can I compile a set of kernel parameters (with this kernel)that will fully support this board and cpu?

---

### Post by bosonflux on 2006-07-05
Is this in the wrong forum or just a hard question?

---

### Post by cptnapalm on 2006-07-05
I wouldn't worry too much about the unknown listing as it does the same for my cpu.  Doesn't have any effect on anything.

List of processor families supported: [http://en.wikipedia.org/wiki/Linux_kernel#Portability](http://en.wikipedia.org/wiki/Linux_kernel#Portability)

(Is it just me or is Google getting less and less usable?  Took me far longer to come up with a relevant link than it once would have.)

---

