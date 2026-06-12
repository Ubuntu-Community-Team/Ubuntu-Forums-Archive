---
title: "Moving PATA drive to SATA drive"
date: 2005-08-12
forum: Desktop Environments
---

### Post by drdabbles on 2005-08-12
_**Introduction**_
This mini-howto will help you move your boot partition from a PATA (IDE) drive to an SATA (Serial ATA) drive. The particular scenario for this document comes from installing Ubuntu on a PATA drive, and then moving your root partition to a SATA drive. If you've tried this already, you have no doubt found that the kernel panics because it has not mounted the root partition because the kernel module has not been loaded.

_**Step 1: Copy your data**_
I assume you have already created your destination partition. If not, there are countless HOWTOs on doing so.

You may use any method to actually copy your data, but I will caution you all to not use tar. There have been bugs identified in how tar works in this process, so I will not detail it here.

[list=1]
[*]Create a mount point for your destination partition
> # mkdir /destination

[*]Mount your destination partition, replacing sda1 with your actual partition:
> # mount /dev/sda1 /destination

[*]Copy the files & directories from your root to the destination mount point:
**NOTE:** using the "a" option tells cp to copy all files and directories, preserving all permissions and attributes it can. Using "x" tells cp NOT to cross over to different filesystems, so no mounted devices will be copied (i.e. /dev)
> # cp -ax / /destination/

[*]Verify everything you want is copied. If you want to move any data that is mounted under root to the destination partition as well, do that *now* or you will regret it.

[*]Edit your fstab file to point Linux to your *new* root partition:
Look for a line like:
**NOTE:** Remember to use your actual device names!
> /dev/hda2       /       reiserfs        defaults        0       1
And change it to read:
> /dev/sda2       /       reiserfs        defaults        0       1

[*]At this point, you would normally be done after a reboot. DO NOT REBOOT!!! You'll be stuck, and hopefully have a livecd handy. If not, go find your install disk.

[*]If your /boot directory is a mounted device, mount it now:
> # mount /boot

[*]Create a new initrd file. This process replaces your initrd file with one that knows about your SATA root device. In other words, THIS is the critical step.
We made our new initrd file in the /tmp directory to keep from overwriting our original...just in case.
> mkinitrd -o /tmp/newinitrd

[*]Backup your original initrd file, and move the new one into action:
> # mv /boot/initrd.img-2.6.10-5-686 /boot/initrd.img-2.6.10-5-686.bak
# mv /tmp/newinitrd /boot/initrd.img-2.6.10-5-686
[/list]

At this point, you should have everything in place and ready to go. Create a new entry for your boot loader that specifies the new root directory.
Adding this entry SHOULD allow you to boot to your old root partition in the case of an emergency...so...DO NOT DELETE IT!
In grub, you'll add this entry:
> title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-686 **root=/dev/sda2** ro quiet splash
initrd          /initrd.img-2.6.10-5-686

_**Wrapup**_
Reboot and make sure everything works correctly. This worked for me after much hairpulling. I had moved partitions and data around several HUNDRED times in the past, but never on Ubuntu. Ubuntu uses the initrd image, and thus the initrd needs to be replaced with one that knows about your SATA devices.

Good luck!

---

