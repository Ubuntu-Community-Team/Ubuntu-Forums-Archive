---
title: "Grub - Error 17 and cannot reinstall"
date: 2006-01-09
forum: General Help
---

### Post by sirluke on 2006-01-09
My configuration is the following:
Dell Inspiron 8600C

-primary disk drive hda 60gb internal (the bootable XP partition is the second, hda2)
-external usb drive, two partitions, the first is NTFS the second, bootable, is ext3 with Breeezy installed

I succesfully installed Breezy on the usb drive, sda2, with Grub on that partition, the only problem I wanted to fix was that when the External disk was connected at boot I could not start XP from the Grub menu, "unknown filesystem" error.
Doing some search on this forum I found some possible workaround to fis the problem,  mainly crossmapping hd0 with hd1. Theese solutions didn't work and finally rendered my system unbootable with Grub error 17.

After that I tried, first, doing a update-grub with no luck: the update goes fine but the error remains.
Then I tried the procedure to reinstall the boot manager from the install CD, going manually through the partition setup and then jumping to the Grub installation step, but it gives a fatal error installing grub on hd1, or sda.

I did not give up and i tried booting the cd in rescue mode and from a shell, after chroot /target I called Grub and tried the following commands:
root (hd1,0) -> unknown filesystem
setup (hd1) -> could not mount

listing the partition with "cat (hd [tab]" I see al partitions of booth disks as unknown filesystem

doing a grub_install /dev/sda it gives an error:
could not read correctly stage1

trying to list the partitions with "fdisk -l" I have no luck because an error occurs: could not find "/proc/partitions"

That is all I've tried.
Really I don't want to reinstall everything, it was running soo good before, so if anyone has a clue he is veeery welcome to help, thanks.
UBUNTU ROCKS, anyway!

Luca

---

### Post by sirluke on 2006-01-10
I couldn't wait, so I just reinstalled Breezy.
I'm stuck with the original problem. I thought I found the solution in theese forums using chainloader(hd1,0)+1, but I cannot find the threads because I lost the browser history in the install process.
'till the next one...

---

### Post by pbb on 2006-01-10
I cannot make sure from your story, did you try reinstalling Grub using the Ubuntu Install CD? I also used to get an Error 17 (after repartitioning my HDD), and it fixed my problem.

I got several error messages from the Install CD, which I had to just ignore and continue. Afterwards, my problems were solved. See here: [http://www.ubuntuforums.org/showthread.php?p=619334#post619334](http://www.ubuntuforums.org/showthread.php?p=619334#post619334)

---

