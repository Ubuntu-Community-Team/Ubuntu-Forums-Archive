---
title: "How do i remove Windows Dual-boot"
date: 2012-04-04
forum: Desktop Environments
---

### Post by Dave_G on 2012-04-04
Hi

I want to remove my Windows dual-boot and use the whole disk for Ubuntu; i'm a bit nervous with removing partitions in case i mess something up!

Could you advise on what i should remove from the below attached screenshot using GParted?

Many Thanks

Dave.

---

### Post by ajgreeny on 2012-04-04
sda1 and sda2 are your windows OS partitions and sda3 is the recovery partition at the end of the disk.

I have no idea how the recovery partition works as I have never had one to use, so I don't know if you can boot to it from grub, or if it is of any value to your computer any more.  I imagine this is Windows 7, as it has a small boot flagged partition, and a large OS partition, and I think it is only usually done this way in Win 7, though I have never used Win 7 so can not really help on that any more.

If you are really sure about removing the windows partitions you can do so by deleting them using gparted, but make sure you only delete those two, and that you have backed up any personal files on them first;  there is 104GB of data on sda2, some of which must be of value to you, I presume.

Moral of this post?  Be certain what you really want; are you sure you will not want windows back in future?  If you might, make sure there is a viable way to use that recovery partition.

And finally, backup any personal files you need before you do anything else.

---

### Post by Dave_G on 2012-04-04
Thanks for the reply.

So just to confirm i delete sda1, 2 & 3. (Windows 7)

sda4, 5 & 6 are my Ubuntu partitions; do i have to unlock those key's next to them to merge them all together?  What do i also do with that unallocated space at the end?

Cheers.

---

### Post by ajgreeny on 2012-04-04
Sorry, I should have explained in more detail.

The three partitions sda4, 5 and 6 are locked because either you are looking at the setup in your installed ubuntu OS, or you are using a live system which automatically finds, mounts and uses the swap partition, which in turn means you can not make any edits to the whole extended partition contents, ie your ubuntu partitions.  Gparted can not work on mounted partitions.

To do anything it is safest to use a live system, open gparted then right click on the swap partition and choose swapoff, then unmount the extended partition sda4.  However if you only want to delete the windows partitions, you will not need to bother with any of that as you will not be acting on the ubuntu partitions.  Also note that you can not combine those ubuntu partitions into just one;  sda4 is just an extended partition, ie a wrapper for other logical partitions, in your case sda5, the OS, and sda6, the swap partition.

If you delete the two windows partitions and the recovery partition, you will have a 400GB unallocated space at the start of the disk and almost 13GB of unallocated space at the end.  You will find it easiest to make new partitions in both those spaces, rather than move the ubuntu partitions, as moving is a very long job and seldom worth doing in my opinion.  The new partitions can be automounted at boot with an edited /etc/fstab file.  Come back after making new partitions if you want to do this.

---

### Post by mathgeek2000 on 2012-04-04
Just for the paranoid -- Many Retail PCs released with Windows 7 let you create only one copy the reinstall disks. -- So if you want to play it extra safe you could use something like CloneZilla to back up the Windows recovery partitions.

That said - what I did on my laptops is install only Ubuntu Linux. After backing up all your data, you can wipe the partition table, and recreate it. Reinstall - under linux the /boot folder could be it's own small partition, and you can make 3 other primary partitions.

Now -- your Linux OS is in an Extended Partition on your PC. -- That also works, -- You could 'move' your existing linux partitions to the beginning of the HDD, and extend them (increase their size) as needed -- but it's more risky.

---

### Post by ajgreeny on 2012-04-05
Personally, I would advise you **not** to make a separate boot partition, as mathgeek2000 is suggesting, as in the long run, it can present you with more problems than it solves.

As long as you are happy letting grub be the bootloader for your system, and I believe that grub 2 is the best bootloader I have seen so far, you can leave boot simply as a folder in the root partition, and let grub install itself in the MBR of the first system disk, ie /dev/sda (note just /dev/sda, not /dev/sda1) which it will do by default.

---

