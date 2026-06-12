---
title: "Disk Warning on Dell Mini 9 with Ubuntu 9.10"
date: 2010-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cerin on 2010-01-28
I had been running the stock 8.04 on my Dell Mini 9 without problems. Then I installed 9.10, and everything seems to work well, except now I'm getting the disk warning, "disk is being used outside design parameters". The "SMART Data" dialog says the disks self-tests pass. Is this warning something I should be concerned about, or is it just some fluke caused by the hard-drive being flash-based?

---

### Post by reabralop on 2010-07-08
I have the same computer and did the same upgrade a while back. The drive is fine and will continue to work. Can't remember how I did it but I got the massage to stop showing and now that I've upgraded to 10.04 I'm getting it again. Hopefully I can find the remedy again.

---

### Post by Cerin on 2010-07-08
I found if I click on the panel warning icon, or go to System->Administration->Disk Utility, you can check/uncheck the feature that warns about problems on the disk.

---

### Post by mikewhatever on 2010-07-08
I don't know if disregarding such a warning is a good idea. Why don't you post the output of **sudo fdisk -l** from a terminal window.

---

### Post by imwithid on 2012-03-02
I've had this warning for the second time and as far as I can tell, I suspect that this is a memory address issue. I do not have the technical expertise to prove it but it takes place only when I have many drives attached or when transferring data between multiple drives.

Currently, I'm re-arranging my data between five hard drives, all over 500 GB (total hard drives capacity is about 3.14 TB).

All drives but one are connected via SATA. Part way through the transfer, I received the notification to check the SMART report for details wherein I saw the "DISK IS BEING USED OUTSIDE DESIGN PARAMETERS" warning.

My system is a 64-bit system, circa 2006 so I suspect that there may be some hardware (or driver) limitations on older 64-bit systems or on current budget systems.

Can anyone verify or discount this theory?

[Edit]

A few minutes later when cross copying was completed, the error had disappeared. This furthers my theory of it being a memory address issue.

---

