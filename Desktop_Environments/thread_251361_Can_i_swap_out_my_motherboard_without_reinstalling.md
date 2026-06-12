---
title: "Can i swap out my motherboard without reinstalling?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by jamespi on 2006-09-05
I'm about to change my crappy PC-Chips Socket A motherboard for a better MSI KT4V. I know on windows swapping out the motherboard is the end of the universe and you have to reinstall most of the time, but i was wondering if linux with its "just works" drivers might just take a new motherboard in its stride.

anyone have any advice? i will try the dapper live cd on the motherboard first to make sure the hardware is supported.

---

### Post by tseliot on 2006-09-05
There's no need to reinstall Linux after you change your motherboard.

It's not Windows :mrgreen:

---

### Post by tkjacobsen on 2006-09-05
Not if you use the default ubuntu kernel. If you have a customized kernel, it might be nessecary to reconfigure and compile the kernel to match your new motherboard

---

### Post by tminuszero on 2006-09-05
> **tseliot said:**
> There's no need to reinstall Linux after you change your motherboard.

It's not Windows :mrgreen:

Be fair tseliot: you can certainly switch out a motherboard with a Windows install. You'll simply have to spend two weeks getting everything working correctly, all the while wishing that you had just reinstalled :-D

---

### Post by jamespi on 2006-09-05
no its just the standard kernel, so it should be fine

---

### Post by djheadley on 2006-09-05
I did basically the same thing a couple of weeks ago.  I got a better computer with no drives or RAM.  All I did was move the drives and RAM and when I booted the computer all I had to reconfigure was xorg (search on that, you'll find the command) and reboot.  I dual boot with WinME and I had to reboot 6 times in order to get it right.  YEAH UBUNTU!!!

---

### Post by bluenova on 2006-09-05
Don't forget to change to the best kernel for your new board:

Intel: 686 or for multi-processing: 686-smp
AMD: K7 or multi-processing: k7-smp

---

### Post by jamespi on 2006-09-05
its another socket a board - i decided against it in the end because i was only swapping because my current board underclocks my chip to 100MHz fsb for no reason. but it turns out the other one does to so i never tried any of this out, but i'm sure it would have worked. thanks for your help.

---

