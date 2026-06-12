---
title: "Safe to run Kaspersky on Win partition of dual-boot Linux box?"
date: 2016-03-27
forum: Desktop Environments
---

### Post by martin172 on 2016-03-27
I know from experience that Kaspersky looks at EVERYTHING on your HD.  If I install Kaspersky AV or TS on the Win7 partition of my dual-boot Ubuntu box, what will Kaspersky do when it encounters my Linux partition?  Is it safe to let Kaspersky scan my Linux files and file system?
Thanks.

---

### Post by sammiev on 2016-03-27
There is no reason why you can not run Kaspersky on Windows while you have Linux on the same HDD.

---

### Post by martin172 on 2016-03-27
Thanks, sammiev.  I will carry on then.  Thanks again for your reply.

---

### Post by sander14 on 2016-04-07
i do not see why not NTFS systems (mainly windows) can not see Ext4 (mainly Linux) partitions

---

### Post by SeijiSensei on 2016-04-08
> **sander14 said:**
> i do not see why not NTFS systems (mainly windows) can not see Ext4 (mainly Linux) partitions

Windows doesn't ship a driver for ext4 (why would they?).  There are [third-party](http://www.ext2fsd.com/?page_id=2) options available.

---

