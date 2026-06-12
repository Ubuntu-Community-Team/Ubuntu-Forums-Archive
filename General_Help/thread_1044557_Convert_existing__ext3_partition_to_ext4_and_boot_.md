---
title: "Convert existing / ext3 partition to ext4 and boot from it with Intrepid"
date: 2009-01-19
forum: General Help
---

### Post by Radomir on 2009-01-19
I need some help here. After a few shots, I was able to compile 2.6.28 kernel following Master Kernel Thread instructions. Did not messed with configuration too much, just enabled Ext4 as module, and everything else in Ext4 section, except debugging. Booted into new kernel, recompiled nvidia-drivers (installed manually) and everything is working smooth. I would like to try to convert my only partition to ext4, but I'm sure this would not work as Intrepid's grub does not support ext4. I saw a grub update in Jaunty which enables grub-legacy to boot from ext4. If I install that package, what should I do to update my existing boot loader? Would it be possible to boot from ext4 then?  I would update /etc/fstab, and I saw a workaround with rootfstype=ext4 in menu.lst. Then I would convert my ext3 partition to ext4 with 8.10 live CD with 
tune2fs -O extents,uninit_bg,dir_index /dev/yourfilesystem
fsck -pf /dev/yourfilesystem (from Kernel newbies).
Would this work? Am I missing something? 
Regards,

---

