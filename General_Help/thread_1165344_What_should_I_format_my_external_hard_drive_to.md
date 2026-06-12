---
title: "What should I format my external hard drive to?"
date: 2009-05-20
forum: General Help
---

### Post by switch10 on 2009-05-20
I'm using Ubuntu 8.10.  I have an external hard drive that is currently formatted to FAT32.  I run windows XP in VirtualBox to sync my IPhone.  I am planning on putting my music on this hard drive, and I want it to be readable, (and preferably writeable) in windows XP.  What format should I use??

Thanks.

Dave

---

### Post by binbash on 2009-05-20
NTFS if you are planning to keep files over 4gb like mkv videos.Else you can use fat32

---

### Post by switch10 on 2009-05-20
Thanks BinBash.

Yea I plan on having files over 4 gigs.

NTFS sounds good then.

---

### Post by megamania on 2009-05-20
> **switch10 said:**
> Thanks BinBash.

Yea I plan on having files over 4 gigs.

NTFS sounds good then.
Depending on which OS you are going to use more often, you can also format it to EXT2/3. There are utilities for Windows which allow you to "mount" an EXT filesystem.

---

### Post by logos34 on 2009-05-20
> **megamania said:**
> There are utilities for Windows which allow you to "mount" an EXT filesystem.

i.e. [fs-driver]("http://www.fs-driver.org/faq.html")

Use ext3--it's better.

---

### Post by switch10 on 2009-05-20
I use ubuntu as my primary OS.  Windows is run in VirtualBox.  I already reformatted to NTFS.  Thanks everyone.

---

