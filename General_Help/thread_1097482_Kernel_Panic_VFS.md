---
title: "Kernel Panic VFS"
date: 2009-03-16
forum: General Help
---

### Post by bharring on 2009-03-16
hey guys,
complete newb to ubuntu here.  Made the switch after I didn't want to deal with actually PAYING for a indecent OS... Anywho I'm having trouble with my primary kernel boot.  I'm using 8.10 with kernel 2.6.27-11 as my primary boot and every time I boot up it tells me [    0.784161] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown- block (0,0)

I'm currently on an older kernel (I think its 2.6.27-7) as I went to grub and changed the kernel I want to use, but I'd really like to be using 2.6.27-11.  After I installed it, I downloaded a lot of upgrades, and did the necessary restart, only to find the error message.  I have a feeling its something with the hard drive that got changed with the updates, but I'm not sure where to begin.
My computer
Intel P4 2GHZ,
625 MB Ram
40 GB HD
NVIDIA GFORCE4MX

A really old computer I know... anywho thanks for the help in advance

---

### Post by AMD64_N_Linux on 2009-03-16
Just got through doing a re-install after XP hosed a partition.

Did a fresh install of Intrepid, rebooted, updated everything, and on the next boot, got the "Kernel Panic - not syncing: VFS: Unable to mount" error.

Tried a 2nd time, same error. Next time I used the previous kernel (?), thanks to someone for grub configuring the old kernel too.

Anyway, hope to hear something soon.

BTW, I would have included the log, but the Kernel panic happens so soon, that I cant find anything in any of the logs.

---

