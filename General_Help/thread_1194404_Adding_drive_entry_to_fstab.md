---
title: "Adding drive entry to fstab"
date: 2009-06-22
forum: General Help
---

### Post by 73ckn797 on 2009-06-22
I want to mount one of my additional drives during boot-up. Looking at my fstab should I just copy and paste the info for my primary drive, / drive? Then change the actual drive details?

I will use this drive for documents only. I found that in Ubuntu Tweak I can designate my Documents location, which I have, to the other drive. When I reboot the drive is not mounted.

here is my current fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2a6f6ef3-b03e-4a52-97e0-9594fbc29574 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Here is the info from fdisk -l on the drive I want to add:
```
/dev/sdc1: LABEL="sdc" UUID="ea630bd4-541e-46f3-ad02-b31ee32d1cea" SEC_TYPE="ext2" TYPE="ext3" 
```How should I write the line for the other drive?

Like this?:
```
/dev/sdc1 /media/sdc ext3 defaults 0 0
```or this:
```
UUID=ea630bd4-541e-46f3-ad02-b31ee32d1cea /Documents    ext3    relatime,errors=remount-ro 0  0
```I include Documents because that is the folder on the drive. Should I use "/media/sdc/Documents" instead?

I am reading the Documentation on fstab but am not clear on this.

---

### Post by michy99 on 2009-06-22
This is what I would use:```
UUID=ea630bd4-541e-46f3-ad02-b31ee32d1cea /Documents    ext3    relatime 0 2
```The advantage of using UUID is that /dev/ designations can sometimes change if you add or remove a drive. Also, if I understand correctly, you want to use this as your Documents folder, so you should mount it there.

---

### Post by 73ckn797 on 2009-06-22
> **michy99 said:**
> This is what I would use:```
UUID=ea630bd4-541e-46f3-ad02-b31ee32d1cea /Documents    ext3    relatime 0 2
```The advantage of using UUID is that /dev/ designations can sometimes change if you add or remove a drive. Also, if I understand correctly, you want to use this as your Documents folder, so you should mount it there.


That looks good. I was not too far off. The last digit (2) is for checking the drive, correct?

Yes, you do understand me correctly. Using the tweak feature works great as long as I do not restart the system. This ought to fix that.

---

### Post by michy99 on 2009-06-22
> **73ckn797 said:**
> That looks good. I was not too far off. The last digit (2) is for checking the drive, correct?

That is correct. I believe that it controls when the drive gets checked, The main / partition should be 1.

---

### Post by 73ckn797 on 2009-06-22
> **michy99 said:**
> That is correct. I believe that it controls when the drive gets checked, The main / partition should be 1.

sda is designated 1

Thanks!

---

