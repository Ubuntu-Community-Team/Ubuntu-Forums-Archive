---
title: "After running recovery mode, no kernel is mountable"
date: 2010-03-21
forum: Desktop Environments
---

### Post by havoc783 on 2010-03-21
I was having a problem with my sound and two oscillating lines at the top of the screen after the 9.10 upgrade. So I read somewhere that running recovery mode, ( the selection from the GRUB ), would fix the problem.  Well it said it finished successfully and sent me to the non-graphical login screen. I logged in and was at a terminal prompt where I rebooted. When I got to the GRUB, any kernel I try to select was unmountable. Any ideas?

---

### Post by quixote on 2010-03-22
9.10 uses Grub2, which numbers the drives differently.  The physical drive #, the first one, starts from zero, like old-grub.  But the partition #, the second one, starts from one.  (Do NOT ask me what the grub devs are thinking.  They're either crazy, or not thinking, or both.)  To boot from the first partition of the first HD in old grub: (hd0,0).  In Grub2, the same thing is (hd0,1)

So the only thing I can think is that maybe recovery mode somehow reverted to the old system, and now the new one can't find the bootable partition anymore.

The Grub2 docs have good info on how to [rebuild your grub]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") from the grub command line, which, really, is the easiest way to do it.  Honest.  It's a bit tedious, but it works.

---

