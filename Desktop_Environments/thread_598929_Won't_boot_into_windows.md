---
title: "Won't boot into windows"
date: 2007-10-31
forum: Desktop Environments
---

### Post by mac71 on 2007-10-31
Is there anybody out there who can help?

I have a dual boot system with windows xp pro. and ubuntu.

I upgraded to Gutsy and all was fine. 
Then I decided to be a clever git and see if I could make wine use my windows partition as its c drive.
BIG MISTAKE (it seems)!

I came out of Ubuntu to boot into windows and couldn't. It shows up on the grub menue, but  Xp wont boot from any options that windows offers(safe mode etc.).  In a state of panic I removed wine and all folders. Still no joy. So, now in a cold sweat, I reinstalled Ubuntu with my Feisty disk to see if it was an issue with it not un-mounting the windows partition.

All the while, with my wifes eyes boreing into the back of my head!

Now, back in Fiesty, my windows partition is permantly mounted. when i try to unmount i get this:

> Cannot unmount the volume.
unmount:/media/sda1 mount disagrees with the fstab.

I feel like I've spent the last 8hrs pushing water uphill, and it looks like the wife might spend some time not talking to me as well.

If you can, PLEASE HELP!!

---

### Post by taurus on 2007-10-31
So Feisty mounts your XP fine and when you want to unmount it, you get an error message!  Is that the problem?

Post the outputs of these two commands from a terminal.

```
sudo fdisk -l  <-- That is a lower case letter l, not number 1.
cat /etc/fstab
```

p.s.  The wife is watching you like a _hawk_ now.

---

### Post by mac71 on 2007-11-01
Hi Taurus, you're not kiddin' mate!
I done that & got this:

> user@Ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5288    42475828+   7  HPFS/NTFS
/dev/sda2            5289        9542    34170255   83  Linux
/dev/sda3            9543        9730     1510110    5  Extended
/dev/sda5            9543        9730     1510078+  82  Linux swap / Solaris
user@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b21a03ab-4abf-4eaa-b532-b72adfc256b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=164C94864C946273 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=17ce9010-dc95-461b-93ca-2e20a190f91f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
user@Ubuntu:~$ 


In answer to your question, being able to freely mount or unmount the windows partition, I'm hoping  I'll then be able to mount and boot at GRUB.

---

