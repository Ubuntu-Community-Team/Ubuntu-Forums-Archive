---
title: "Flash Install GRUB Error 18"
date: 2009-03-04
forum: General Help
---

### Post by radams8 on 2009-03-04
Hi all,

So I am an absolute beginner at anything linux but it seemed interesting so I decided I would install it.  I installed it on an 8 GB flash drive by using the guided install to take up the entire flash drive, then installing the boot loader to the same drive rather than my hard disk.

All installed well, so I restarted to give it a try.

Then came GRUB error 18.

I have read online about some cylinder size and moving files and whatnot... but I'm not exactly sure what that means.  Can someone dumb it down for a linux noob?  And maybe help me solve the problem while you're at it?

Thanks.

---

### Post by ajmorris on 2009-03-05
hi there,
GRUB error 18 occurs when the selected cylinder exceeds the max supported by your BIOS. This error *usually* occurs when you install grub to a disk, that is larger than your BIOS can handle. However, it is more likely in your case, that grub cannot start executing your kernel, because your kernel is in a block that grub cannot access.
You can solve your issue if you create a boot partition at the beginning of your flash disk (if i remember correctly, you will want it entirely within the first 1023 cylinders of your flash disk (google it to make sure if you wish :))

So, boot up your ubuntu live cd (or ubuntu installed on your partition, it doesnt matter as you are not resizing your mounted harddrive), and run the application 'gparted' from the menus. You will need to change the device from the 'File' menu to your flash disk (probably /dev/sdb). Then resize your ubuntu partition to make room for a boot partition. The boot partition does not have to be too large, as it will only contain your grub files, and your kernel bzImage and initrd. (your ubuntu bzImage file will be ~4mb and your ubuntu initrd ~8mb)

Then re-order your partitions so that your boot partition is at the beginning of your partition table. Apply the changes, and reboot.

AJ

---

