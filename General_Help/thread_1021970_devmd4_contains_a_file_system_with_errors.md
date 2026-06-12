---
title: "/dev/md4 contains a file system with errors"
date: 2008-12-26
forum: General Help
---

### Post by uygaruzunhasan on 2008-12-26
:confused:
urgent. I use it as server in office and all bussiness has been freezed
I got 6 hdd using with soft raid varations.
Last weekend, electrics cut for a day and ups can't shutdown the system on time. Because of that on of the hdd demaged. My main OS is Ubuntu. When I try to boot, It fails on "fsck". I also tried it with Fedora6 but nothing changed. it says:
/dev/md4 contains a file system with errors,check forced

When it asked: Resize inode notvalid. Recreate<y>?
I said yes then It said and stay said:
/dev/md4 contains a file system with errors,check forced
Pass1: Checking inodes, blocks, and sizes

What could I do?

---

### Post by fjgaude on 2008-12-26
Use backup. Re-create the array, then take out the bad drive using mdadm's -f and -r commands. Copy backup to new array.

---

### Post by uygaruzunhasan on 2008-12-26
> **fjgaude said:**
> Use backup. Re-create the array, then take out the bad drive using mdadm's -f and -r commands. Copy backup to new array.

Thank you. I gonna do it at weekend, I just dismount one HDD(the damaged one)  then system booted normally with no loose because it was one of the pair of RAID 1

---

### Post by fjgaude on 2008-12-26
Please, please, for important data always have backups: here we have online, near-line, and off-line backups.

So happy you got out of the trouble you were in.

---

