---
title: "Discussion - https://help.ubuntu.com/community/UEFI"
date: 2012-09-10
forum: Documentation and Community Wiki Discussions
---

### Post by YannBuntu on 2012-09-10
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Support threads/questions should be posted in normal forums.

Thank you.
__________________

---

### Post by oldfred on 2012-09-10
Yann,

If you just install Ubuntu in BIOS mode, it will normally be MBR partitioning. With UEFI it should be gpt partitioning.

Windows will only install on gpt partitioned drives with UEFI. 

Ubuntu will install in BIOS mode to gpt or MBR drives.  Default is only gpt for drives somewhat over 1TB, but if not dual booting with Windows on BIOS based computers gpt can be used on any drive. The Arch site also recommends gpt for SSD drives.

Drives over 2TiB or about 2.2TB have to be gpt partitioned to use entire drive.

---

### Post by YannBuntu on 2012-09-10
Agreed.

(Please let me know if one day you see a Mac using GRUB as main bootloader)

---

