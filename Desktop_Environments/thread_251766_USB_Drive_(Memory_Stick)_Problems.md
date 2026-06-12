---
title: "USB Drive (Memory Stick) Problems"
date: 2006-09-05
forum: Desktop Environments
---

### Post by saehn on 2006-09-05
Hello all, this has come up before at least once in the forums, but I can't find any real resolution for it.

I'm using Dapper 6.06. I have a standard SanDisk USB Mini Cruzer, 256mb. It work fine the first time I plug it in, full read/write/execute access. But, if I "eject" it by right clicking on its icon from the desktop, Ubuntu doesn't automatically detect it the next time I plug it in.

I have successfully used "sudo mount /dev/sda1/ /mnt". This resulted in the drive's contents being accessible in /mnt. However, I really want full capability for reinserts, and I'd like to know how I can achieve that. 

Can anyone help?

Thanks,
saehn

---

### Post by saehn on 2006-09-05
One other thing... when I used that mount command, the /mnt contents are only read-accessible. This makes it a less than ideal solution (compared to the original functionality).

---

