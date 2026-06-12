---
title: "Diagnose boot prblems"
date: 2009-05-26
forum: General Help
---

### Post by pantone186 on 2009-05-26
Hello,

Can anyone give me some pointers diagnosing boot problems.


My system can be left running for days when booted but requires anything from 3 to 8 attempts to boot. I can hear the HD begin to read but then stop.


Intrepid Ibex
2.6.27-14-generic SMP x86_64 GNU/Linux

---

### Post by whoop on 2009-05-26
Once booted correctly edit menu.lst
```

sudo nano /boot/grub/menu.lst

```
remove "quiet splash" from the kernel line you are booting from..... Next time it locks up you can see where it gets stuck and troubleshoot further.

---

