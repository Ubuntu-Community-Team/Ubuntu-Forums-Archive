---
title: "removing OS"
date: 2008-12-24
forum: General Help
---

### Post by unknown25 on 2008-12-24
**Can Any One Help Me How To Remove Ubuntu !I Have The CD Of Ubuntu!So Is It Possible To Remove it From The CD?**:confused:

---

### Post by cariboo on 2008-12-24
Boot from the LiveCD, and once at the desktop go to System-->Administration-->Partition Editor. and remove the partitions created by Ubuntu. Then boot from your Windows install disk and go into the recovery console and run FIXMBR and FIXBOOT.

Once you are back in Windows you can partition and format the empty hard drive space, so that it is usable again.

Jim

---

### Post by taurus on 2008-12-24
Yes, you can remove Ubuntu partitions with the LiveCD.  However, is that machine dualboot (windows and Ubuntu)?

Because if it is, then it's best to boot into windows and fix the bootloader first or else you won't be able to boot into windows once you delete Ubuntu partition since GRUB will complain about it.

The command to fix the bootloader in windows (terminal) is

```
/fixmbr
```
Then, you can use gparted from the LiveCD to delete Ubuntu.

---

### Post by unknown25 on 2008-12-25
but i dont hav an windows CD ....So now wat>?

---

### Post by oilchangeguy on 2008-12-25
> **unknown25 said:**
> but i dont hav an windows CD ....So now wat>?

spell check, and find a friend with a windows cd. also check out this link:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
from there you can't create a bootable cd. and use it to fix the windows boot record.

---

### Post by kaykelkar on 2008-12-25
so guys if i understand it correctly then....
[LIST=1]
[*]Remove Ubuntu Using the Live CD
[*]Then Boot with a WinXP bootable CD
[*]Then fix the windows boot loader
[*]Finally, convert the freed partition into FAT32 drive
[/LIST]

Why dont we put these kind of generic question & answers on a sticky post??

---

### Post by oilchangeguy on 2008-12-25
> **kaykelkar said:**
> so guys if i understand it correctly then....
[LIST=1]
[*]Remove Ubuntu Using the Live CD
[*]Then Boot with a WinXP bootable CD
[*]Then fix the windows boot loader
[*]Finally, convert the freed partition into FAT32 drive
[/LIST]

Why dont we put these kind of generic question & answers on a sticky post??

4. only if you want to. you can also partition it ntfs, or just use the live cd to expand the windows partition to use the unallocated space.

---

### Post by ugm6hr on 2008-12-25
> **unknown25 said:**
> but i dont hav an windows CD ....So now wat>?

Try this: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by taurus on 2008-12-25
Wouldn't it be easier (since you've claimed you don't have a windows CD) to

1.  boot into windows and fix the MBR,
2.  reboot to make sure it boots directly into windows instead of seeing the GRUB menu,
3.  reboot with the LiveCD and delete the Ubuntu partitions,
4.  convert those partitions into one partition and format it to ntfs filesystem,
5.  reboot without the LiveCD.

---

