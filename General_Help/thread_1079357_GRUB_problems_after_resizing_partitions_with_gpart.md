---
title: "GRUB problems after resizing partitions with gparted"
date: 2009-02-24
forum: General Help
---

### Post by BryanKeith on 2009-02-24
Hello,

I used gparted to resize sda3 and sda1.  Now when I power on the machine, it says "GRUB" in the top left corner but doesn't get any further than that.  I let it sit there for hours.  What can I do?

More background: I used partimage to save an image of sda1 and sda3.  Then I used gparted to make sda3 smaller, moved the swap partition to the right, and increased the size of sda1 from ~5.6GB to ~56GB.  I used systemrescuecd for all that stuff.

Any help is appreciated.  I'm not sure what to do.  I have considered using partimage to rewrite sda1 to the newly sized partition, but I thought I'd check here first to see what people recommend.

Thanks for the help,

Bryan

---

### Post by Coreigh on 2009-02-24
By moving partitions you re-ordered them. If you had 3 partitions and the middle was swap (sda2) and you moved it to the end (right) it is now sda3, and what was sda3 is now sda2. Grub is confused. You will have to boot a LiveCD and edit grub.conf (~menu.1st) in the /boot/grub directory on sda1 (assuming sda1 is the boot partition) to reflect the changes you made.

---

### Post by makisupa123 on 2009-02-24
First make sure that the correct/any partition is set as bootable (or "Active").

Secondly,
Boot to a live CD (gparted should be fine) and look at your grub config (/boot/grub/menu.lst) on your ubuntu drive.  We don't care about all the comments.  

Then, describe your current partition layout in a little more detail.

```
sudo fdisk -l *device*
```

--Mak

---

### Post by makisupa123 on 2009-02-24
Coreigh idea is quite plausible/likely.  Giving us the information in my post will help us determine that.


--Mak

---

### Post by BryanKeith on 2009-02-24
Not realizing that the order the partitions was important, I can see that I wasn't clear in my first post.  With gparted I did not move sda2 to the right of sda3.  I made sda3 smaller by moving the left side to the right.  I moved sda2 to the right into the new empty space where sda3 used to be.  sda2 was still to the left of sda3.  I expanded sda1 by moving the right side to the right into the space where sda2 used to be.

The output of fdisk -l looks ok to me.  sdb, sdc, sdd are external hard drives for data storage.  sde is a stick that I'm using to get data off that machine for this e-mail.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d606

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7104    57062848+  83  Linux
/dev/sda2            7105        7591     3911827+  83  Linux
/dev/sda3            7592       30401   183221325   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8178b532

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001a7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc15ced42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

Disk /dev/sde: 1036 MB, 1036517376 bytes
2 heads, 63 sectors/track, 16067 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0070d2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       16068     1012208    b  W95 FAT32

Here are the non-commented lines in /boot/grub/menu.lst  I have no idea what they mean.

grep -v "^#" menu.lst

default         0
timeout         3
hiddenmenu

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=18ae9e50-1a9b-4391-af3
a-4a4b52624c13 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

Bryan

---

### Post by caljohnsmith on 2009-02-24
How about reinstalling Grub to the MBR of your Linux drive by doing the following:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of the above commands before typing "quit", reboot, and let us know what happens on start up. We can work from there if you want.

---

### Post by BryanKeith on 2009-02-24
> **caljohnsmith said:**
> How about reinstalling Grub to the MBR of your Linux drive by doing the following:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of the above commands before typing "quit", reboot, and let us know what happens on start up. We can work from there if you want.

I didn't think I did this correctly since I was working as root on the systemrescuecd.  How did it know I didn't want to change the MBR for that installation?  At any rate, it worked.  I didn't need "sudo".  Output looked like this (there may be typos since I wasn't able to copy and paste):

grub> root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists ... yes
Checking if "/boot/grub/stage2" exists ... yes
Checking if "/boot/grub/e2fs_stage1_5" exists ... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)" ... 17 sectors are embedded.
Succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0) /boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit

I assume I edited something on sda1 /boot/grub on not /boot/grub for the CD, but how did it know?

Thank you very much.  This worked.  If you don't mind, please explain what I did here and what was wrong so I can try to understand.  Thanks.

Bryan

---

### Post by caljohnsmith on 2009-02-24
> **BryanKeith said:**
> I didn't think I did this correctly since I was working as root on the systemrescuecd.  How did it know I didn't want to change the MBR for that installation?

I assume I edited something on sda1 /boot/grub on not /boot/grub for the CD, but how did it know?

Basically what those commands did is reinstall Grub to the MBR of the sda drive and configure Grub to point to the sda1 partition for its boot files. Whenever you run Grub commands in linux, the following is generally true:
```
(hd0)   = sda
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
(hd1)   = sdb
(hd1,0) = sdb1
...etc.
```
So when you were in the Grub command line, (hd0,0) is your sda1 partition, and (hd0) is the MBR of the sda drive; that's how Grub knew to install Grub to the MBR of your sda drive and not your Live CD. Anyway, glad to hear that worked OK; cheers and enjoy your Ubuntu install. :)

---

### Post by BryanKeith on 2009-02-24
> **caljohnsmith said:**
> Basically what those commands did is reinstall Grub to the MBR of the sda drive and configure Grub to point to the sda1 partition for its boot files. Whenever you run Grub commands in linux, the following is generally true:
```
(hd0)   = sda
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
(hd1)   = sdb
(hd1,0) = sdb1
...etc.
```


Ah, thank you for the elucidation.  ubuntu is running happily again.

Bryan

---

