---
title: "Recovering deleted folder"
date: 2009-05-21
forum: General Help
---

### Post by Robbyx on 2009-05-21
I accidentally deleted my Thunderbird profile. The partition is still sound and all other directories remain.  It was stored on a 3ware raided hard drive. It is not the system drive. The partition is NTFS. 


Based on advice on recovering data in Ubuntu, I ran testdisk in order to restore the missing files. It should show an option to restore directories or files. On the support web site the pictures show an undelete button. It does not appear when I run their filesystem utilities.

I have just written to the author for support but he is on holiday.

I would like to undelete the deleted files and directories but do not know how to do it. Can you help?

The relevant entry for the drive in fstab is:

> UUID=724E07853D78E7A8                    /media/mydocs    ntfs   user,rw,auto,exec,nls=utf8,unmask=007 0 2

Has this anything to do with the undelete button not appearing?

I am using Ubuntu 8.10.

---

### Post by kooldino on 2009-05-23
Ditto, I'm having the exact same issue.

---

### Post by kooldino on 2009-05-23
Try PhotoRec

---

### Post by Robbyx on 2009-05-23
I hope that someone will come along and help us both. Is your problem with a deleted Thunderbird profile?

---

### Post by Robbyx on 2009-05-23
> **kooldino said:**
> Try PhotoRec


It was useless in the context of the TB profile because it does not recover the files in their original names or in their original directories.

---

### Post by kooldino on 2009-05-24
> **Robbyx said:**
> It was useless in the context of the TB profile because it does not recover the files in their original names or in their original directories.

Yeah, that's what I don't like about it. :(

---

