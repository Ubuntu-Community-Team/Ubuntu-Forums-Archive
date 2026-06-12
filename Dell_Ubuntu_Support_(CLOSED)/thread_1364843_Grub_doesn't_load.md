---
title: "Grub doesn't load"
date: 2009-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rementec on 2009-12-26
Hey guys

I just installed Ubuntu 9.10 64 bit with Windows 7 64 bit, windows 7 being the primary install, and I restarted once and Grub worked, but now i get the error message

[I]GRUB loading.
error: no such disk
grub rescue>[/I]

I tried the /fixmbr repair, but the command doesn't work 
I tried to do a general startup repair from the windows 7 disk but that did not work

One other thing that I occurred during the install, my external HD was plugged in during the process and ended up being partitioned, and I reformatted it and rejoined the partitions in windows after Ubuntu was install completed, and I unplugged the hard drive when I restarted the computer and it did not work

What should I do?

---

### Post by bobcollard on 2009-12-27
> **rementec said:**
> Hey guys

I just installed Ubuntu 9.10 64 bit with Windows 7 64 bit, windows 7 being the primary install, and I restarted once and Grub worked, but now i get the error message

[I]GRUB loading.
error: no such disk
grub rescue>[/I]

I tried the /fixmbr repair, but the command doesn't work 
I tried to do a general startup repair from the windows 7 disk but that did not work

One other thing that I occurred during the install, my external HD was plugged in during the process and ended up being partitioned, and I reformatted it and rejoined the partitions in windows after Ubuntu was install completed, and I unplugged the hard drive when I restarted the computer and it did not work

What should I do?
Just an observation:  When you intalled Ubuntu, did you look at the drive choices during installation?  Quite often the second drive will receive the new system instead of the primary and/or the grub.  In that case you would need to have it plugged in for grub to find.  If you have repartitioned that drive it is invisible to grub now when it is plugged in.  Do you still have access to your Windows 7 partition?

---

