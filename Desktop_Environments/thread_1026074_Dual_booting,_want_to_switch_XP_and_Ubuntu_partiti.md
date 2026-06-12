---
title: "Dual booting, want to switch XP and Ubuntu partitions"
date: 2008-12-30
forum: Desktop Environments
---

### Post by gecko3940 on 2008-12-30
I have a dual boot system with a fairly small internal drive (55GB), and a USB external drive (160GB) used mainly for backups. The internal drive /dev/sda has XP on first partition (sda1), then Ubuntu 8.04 (sda2), then linux swap partition (sda5), then a documents partition (sda3).

The XP and Ubuntu partitions are (or nearly are) identical in size at around 17GB before formatting. As I use Ubuntu a lot more, I was wondering if it is worth switching their partitions to increase its speed. If so, I would have Ubuntu first, then swap, then xp then documents. I was thinking of using Gparted and perhaps copying a partition, but am not really sure of the best way. 

Also, are there bootup issues to consider?

Is it worth the bother?

I don't really want to reinstall anything or upgrade unless I have to.

Thanks for any help.

---

### Post by fiddler616 on 2008-12-30
I'm no expert, but I think the time, trouble and potential failure are a lot bigger than the slight speed increase. Just remember you want to do this if you reinstall Ubuntu at some point.

---

### Post by caljohnsmith on 2008-12-30
I would not recommend actually "switching" the Ubuntu and XP partitions, because moving the starting point of the Windows partition will unfortunately break Windows. Instead you could shrink the Windows partition and then grow the Ubuntu partition with that space, assuming the XP and Ubuntu partitions are physically next to each other on the drive. Would that maybe work for you?

---

### Post by fiddler616 on 2008-12-30
> **caljohnsmith said:**
> I would not recommend actually "switching" the Ubuntu and XP partitions, because moving the starting point of the Windows partition will unfortunately break Windows. Instead you could shrink the Windows partition and then grow the Ubuntu partition with that space, assuming the XP and Ubuntu partitions are physically next to each other on the drive. Would that maybe work for you?
[massive delete, due to misreading the previous post]
After thinking some more, I'm pretty sure this is going to involve copying one of the partitions onto some temporary thing, moving the other, and then copying the first back from the temporary storage. carljohnsmith has saved my tail twice about booting Windows, so I'd heed the warning about moving the starting point of Windows. In short: I still don't think it's worth it.

---

### Post by fiddler616 on 2008-12-31
(By the way, you should probably move this out of the "Desktop Environments" category...)

---

### Post by gecko3940 on 2009-01-03
Thanks for the help, I'll consider doing this switch when next install either OS. 

By the way, I'm not sure how to move category, or which category to move it to.

---

### Post by fiddler616 on 2009-01-03
> **gecko3940 said:**
> Thanks for the help, I'll consider doing this switch when next install either OS. 

By the way, I'm not sure how to move category, or which category to move it to.
Well now it's water over the dam--you wanna go to Thread Tools>Mark as Solved.
But for future reference, you hit the report button (near the avatar) and type out a polite note asking for a move. This seems like a "General Help" to me...

---

