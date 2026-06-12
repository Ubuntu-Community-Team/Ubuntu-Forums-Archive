---
title: "Disk check frequency"
date: 2009-04-20
forum: General Help
---

### Post by davidself1001 on 2009-04-20
My system seems to do a disk check once a week or so.  How can I change that to be once a month?

---

### Post by michy99 on 2009-04-20
By default, the disk is checked every 30th mount. You can use tune2fs to adjust this.

---

### Post by davidself1001 on 2009-04-20
Thanks.  How do I do this for a NTSF partition?

---

### Post by ezsit on 2009-04-20
Have you had a look at this help page:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

It could help you edit the fstab file to avoid running fschk on your NTFS drive.

---

