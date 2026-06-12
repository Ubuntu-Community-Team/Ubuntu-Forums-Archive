---
title: "Kubuntu Herd2 Alternate CD - HP Compaq nx7400 EY505ES"
date: 2007-01-21
forum: Development CD/DVD Image Testing
---

### Post by grybba on 2007-01-21
I installed Kubuntu without  many problems. The following things are not working for me:

1. the DSDT.aml is not loaded by default, although I put it the initrd file, (worked on Ubuntu 6.10)
2. I was looking forward to the suspend to RAM on the new kernels - the suspend works, but neither Display nor keyboard wakes up - I am able to shut down using the power button, so the Linux itself wakes up I assume.
3. HAL is not recognizing my ACPI brightness adjustment and neither does the power manager which is a BIG drain on my battery life.

I will be happy to run extra tests, or anything that can help.

---

### Post by pochu on 2007-01-21
> **grybba said:**
> I will be happy to run extra tests, or anything that can help.


You can help reporting these bugs at [Launchpad]("http://bugs.launchpad.net") :D but first, see if they have been reported.

Maybe for the kernel problem you should report it on bugzilla.kernel.org

Thanks
Pochu

---

