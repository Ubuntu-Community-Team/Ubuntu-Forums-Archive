---
title: "Advantages of kernel-3.2.0-30  over 3.2.0-27? [64-bit]"
date: 2012-09-11
forum: Desktop Environments
---

### Post by lucacerone on 2012-09-11
Dear all as I explained in a different post ([http://ubuntuforums.org/showthread.php?t=2053656](http://ubuntuforums.org/showthread.php?t=2053656)),
after upgrading the kernel from the 3.2.0-27-generic to more recent ones I have started having issues with hibernation.

As I couldn't find a solution to this,
I am planning to revert to 3.2.0-27, unless there are very good reasons to keep them. 

So what are the main advantages of having kernel 3.2.0-30 over 3.2.0-27??

Thanks a lot in advance for your help,
Cheers, Luca

---

### Post by Bucky Ball on 2012-09-11
I would suggest you keep the -30 kernel around and just boot from the -27 for now. Keep doing the updates and next time you notice one for the -30 perhaps give it a try after updating. It may be something that will be fixed shortly or may be more serious and perhaps you could dig deeper or report a bug on Launchpad (a report may already exist).

You can easily rearrange the order of kernels (and default kernel) with Grub Customiser, for one, to put -27 back at the top of the list:

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by lucacerone on 2012-09-11
Thanks I used your advice :)

---

