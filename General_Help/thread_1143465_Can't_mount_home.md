---
title: "Can't mount /home"
date: 2009-04-29
forum: General Help
---

### Post by hopelessone on 2009-04-29
Hi,

[https://help.ubuntu.com/community/UbiquityEncryptedFilesystems](https://help.ubuntu.com/community/UbiquityEncryptedFilesystems)

After the install i can't mount /home in LUKS...I get gnome complaining there is no /home attached...

here is my fstab:
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sdc3_crypt /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=80845a4f-0aea-42af-9038-716b9cc1a294 /boot           ext3    relatime        0       2
/dev/mapper/home_crypt /home           ext3    defaults        0       0
Crypttab:
> sdc3_crypt /dev/disk/by-uuid/1e0eb230-5dee-4f73-b752-4507819f7c93 none luks
home_crypt /dev/disk/by-id/scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40208476-part4 none luks

I am stumped....

How can i fix this?

If i log into failsafe console and 
> sudo cryptsetup luksOpen /dev/sdc3 home_crypt
it gives me the error:
> dm_task_set_name: Device /home_crypt not found

What should i do?

Thanks

---

### Post by hopelessone on 2009-04-30
Oh the disk ID changed...?! i thought it was only UUID that changed...

Fixed now..

---

