---
title: "Bootloaders....XP, Vista and GRUB,"
date: 2009-06-08
forum: General Help
---

### Post by szd on 2009-06-08
Okay guys, hi first of all, my first post here. I'm fairly inexperienced with Ubuntu, I currently have 7.10 or Gutsy Gibbon.

So here is my situation, I had Windows Vista, I dualbooted with Ubuntu and everything was fine. All of a sudden Ubuntu stopped working, so I went into Vista and reformatted Ubuntu's partition. Stupid me! I turned on with a Grub error 17, hoping everything would go back to normal.

Anyway I attempted to reinstall Ubuntu but the disc was scratched, and I needed some files desperately from my HD, so I installed Win XP on Ubuntu's old partition. So now I can't get into Vista, GRUB is gone, but I have a Win XP bootloader with only XP as an option.

So now I fix the Ubuntu CD (make a new partition) and install that, now I have GRUB with Ubuntu and Vista as options. Perfect right?...Wrong. The Vista option loads up as XP! So I go into Ubuntu and delete XP partition, so I have 2 partitions. Now I have GRUB with Ubuntu and Vista as options and the XP bootloader comes up, I don't have XP and Vista wont come up even thought I added it in boot.ini.

So the question...how do I get rid of the XP bootloader?

I did not receive a Vista CD with my PC and EasyBCD did not work on XP (got some stupid error).

Now I have several Photoshop documents to complete for school and I have no clue on GIMP, someone please help me.

Many thanks, Szd.

---

### Post by Entropy_Sam on 2009-06-08
Could you post the contents of **/boot/grub/menu.lst**, **/boot/grub/device.map** and   the results of **sudo fdisk -l** so we can see what your current set up looks like? Also let us know which partitions house which operating systems.
 
Thanks!

---

### Post by szd on 2009-06-08
Thanks for the response :)

[B]/boot/grub/menu.lst

[/B]is

> ## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d6d3d94f-ec26-412e-8d61-8b826061a3fb ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d6d3d94f-ec26-412e-8d61-8b826061a3fb ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader

Well that's the end bit which I think you are interested in.

**/boot/grub/device.map** 

> (hd0)    /dev/sda

[B]sudo fdisk -l

[/B]> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6c7198f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13918   110259200    7  HPFS/NTFS
/dev/sda3           13919       14593     5421937+  83  Linux

And I have 4 partitions one one HD.

1.. Was already made, had important manufacturer stuff on it.
2. Windows Vista
and 3. Ubuntu 7.10.

Thanks again!

---

### Post by logos34 on 2009-06-08
Here's a Vista recovery CD download that hopefully will allow you to boot back into windows. Then you can install EasyBCD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by szd on 2009-06-08
Wow thanks mate that looks promising! Will I be able to get onto Ubuntu after I restore Vista's bootloader?

---

### Post by logos34 on 2009-06-08
Once you restore vista boot, you can install EasyBCD, which will allow you to add linux/ubuntu boot entry to windows menu.

good luck

---

### Post by szd on 2009-06-10
Hey, I'm back, that worked! I am now on Vista however there is still a bit of a problem.

Now I have... Grub Menu (then I select Vista) which leads to Vista Bootloader..how do I get rid of the Grub Bootloader? I tried through EasyBCD but I can't get rid of it.

---

### Post by logos34 on 2009-06-10
overwrite grub on the MBR with vista bootloader

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD)

---

### Post by szd on 2009-06-11
Worked perfectly, thankyou!

---

