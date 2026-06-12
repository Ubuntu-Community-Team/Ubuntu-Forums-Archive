---
title: "Kernel Lockup NEED SERIOUS HELP"
date: 2007-09-12
forum: Desktop Environments
---

### Post by kinoka2k on 2007-09-12
THIS IS A FRESH INSTALL.

AMD X2 4400+
1gb Cosair ram
Asus A8N Premium SLI
Nvidia 7800gt

I recieve this error and its flooding my logs and Ive looked around forever for this (google etc) and cannot find a solution.  I beileve its a kernel problem and I have some output that its repeating.

Version of kernel:
Linux K2K 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

kern.log Error Message:

kernel: [18469.876000] BUG: scheduling while atomic: swapper/0xffff0000/0
kernel: [18469.876000]  [schedule+1528/2704] __sched_text_start+0x5f8/0xa90
kernel:[18469.876000][smp_apic_timer_interrupt+117/128]smp_apic_timer_interrupt+0x75/0x80
kernel: [18469.876000]  [apic_timer_interrupt+40/48] apic_timer_interrupt+0x28/0x30
kernel: [18469.876000]  [default_idle+0/96] default_idle+0x0/0x60
kernel: [18469.876000]  [cpu_idle+141/208] cpu_idle+0x8d/0xd0

If you need anything else let me know, but I really really want to fix this as Ive found many people have had this issue, but none have resolves.

---

### Post by kinoka2k on 2007-09-13
bump for help.

---

