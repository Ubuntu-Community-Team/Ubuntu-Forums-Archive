---
title: "Can't boot back into Windows XP"
date: 2006-03-02
forum: Desktop Environments
---

### Post by gsplsngr on 2006-03-02
I am running a dual boot system on a dell inspiron 1000.  At first I could not boot into linux and used boot magic to force it to boot into linux now I can't boot into windows xp...When I try, I first get an error message autochk.exe not found and then it goes to a screen that says stop: c000021a {fataly system error} session manage initialzation system process terminated unexpectedly with a status of 0xc000003a....... I think I can fix the problem of the missing autochk.exe program but can not boot from a cd rom and run boot magic and don't know how to get to dos and try and run it from there.

---

### Post by gsplsngr on 2006-03-09
Found the fix after much searching and here is what it is

[http://www.linuxcompatible.org/stop_c000021a_%7BFatal_System_Error%7D_--_newb_meets_minor_heart_attack..._seeks_me_t31439.html](http://www.linuxcompatible.org/stop_c000021a_%7BFatal_System_Error%7D_--_newb_meets_minor_heart_attack..._seeks_me_t31439.html)

before you reach for any recovery disks, emergency boot disks, Windows installation CD or impact maintenance tools, try entering this at the grub 

command line: unhide (hd0,0)
unhide (hd0,1)
unhide (hd0,2) .. and so on until you run out of partitions.


Did this and it worked like a champ:mrgreen:

---

### Post by user2037 on 2007-10-04
Same Windows XP behavior after a Feisty install to an encrypted partition. However, unhide does not work in my case. Feisty works well enough.

edit: Solution found. In my case the NTFS partition type had been changed to "Linux" (82) instead of NTFS (07). Running Cfdisk from a rescue CD allowed me to change the type back to NTFS. Now Windows boots as expected.

---

