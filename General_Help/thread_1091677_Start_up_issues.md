---
title: "Start up issues"
date: 2009-03-09
forum: General Help
---

### Post by C-130 on 2009-03-09
Can anyone help me fix my ubuntu?

When I start it after a hard reboot it begins a check on the file system it says failed at check 1/5. And I have no idea how to repair ubuntu.

Please help!!!!!!!!!!

Also i know you'll need more information so please ask away.

---

### Post by taurus on 2009-03-09
Did you install Ubuntu on it own partition or did you install it from windows--wubi?

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by C-130 on 2009-03-09
How do i dot his if I have no GUI?

---

### Post by RedSingularity on 2009-03-09
You shouldn't need a GUI to do these commands.  When you boot dont you get the command line interface?

---

### Post by C-130 on 2009-03-09
Yes I do. AFter the checks. i get a black screen with a lot of writing which means little to me followed by  a rather large red [FAIL]

---

### Post by taurus on 2009-03-09
1.  Can you boot into recovery mode from GRUB menu?

or

2.  Can you boot your machine with Ubuntu LiveCD?

---

### Post by C-130 on 2009-03-10
Here is my given output

To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.



ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xe18556c3



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       59572   478512058+  83  Linux

/dev/sda2           59573       60801     9871942+   5  Extended

/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo blkid

/dev/sda1: UUID="32d07499-d412-4f3a-84dc-04976596d3fe" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sda5: UUID="f2030008-fc72-46d5-8b65-9803743804be" TYPE="swap" 

/dev/loop0: TYPE="squashfs" 

ubuntu@ubuntu:~$ cat /etc/fstab

aufs / aufs rw 0 0

tmpfs /tmp tmpfs nosuid,nodev 0 0

/dev/sda5 swap swap defaults 0 0

ubuntu@ubuntu:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on

tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile

tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile

tmpfs                 1.7G     0  1.7G   0% /lib/init/rw

varrun                1.7G  100K  1.7G   1% /var/run

varlock               1.7G     0  1.7G   0% /var/lock

udev                  1.7G  2.9M  1.7G   1% /dev

tmpfs                 1.7G  104K  1.7G   1% /dev/shm

rootfs                1.7G   44M  1.6G   3% /

/dev/scd1             699M  699M     0 100% /cdrom

/dev/loop0            676M  676M     0 100% /rofs

tmpfs                 1.7G   12K  1.7G   1% /tmp

ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-10
```
sudo fsck /dev/sda1
```

---

### Post by C-130 on 2009-03-10
Here is an output for that command.

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 


I am running these through the live disk.

---

### Post by taurus on 2009-03-10
I don't see it mounted from your **df -h**?

Answer no to that question and try to unmount it first if it is really mounted.

```
sudo umount /dev/sda1
sudo fsck /dev/sda1
```

---

### Post by C-130 on 2009-03-10
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 


That is the output. Thank you for all this help.

---

### Post by C-130 on 2009-03-10
Bump.

Does anyone have any help for this?

---

### Post by taurus on 2009-03-10
```
sudo fdisk -lu
```

---

### Post by C-130 on 2009-03-10
And the output is:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sdf: 503 MB, 503840256 bytes
4 heads, 32 sectors/track, 7687 cylinders, total 984063 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0f9998a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              32      984062      492015+   e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-03-10
Whatever happens to your /dev/sda?  I assume /dev/sdf1 is your external thumbdrive or something similar to that.

Perhaps it's time to reboot and get into the BIOS and see if your harddrive is even listed in there.

---

### Post by C-130 on 2009-03-10
I've checked that and yes the hard drive is listed. And in the live CD I have the hard drive and partitions recognised. I really want to avoid another reinstall. And buying a new hard drive. Again thanks for the perseverance in this matter.

---

### Post by pastalavista on 2009-03-10
Try booting from the live CD and run fsck from there...

---

