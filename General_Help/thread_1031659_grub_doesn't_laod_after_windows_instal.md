---
title: "grub doesn't laod after windows instal"
date: 2009-01-05
forum: General Help
---

### Post by chaosdesigner on 2009-01-05
hi,

I've just done my monthly windows wiping and now I have the porblem that grub doesnt load. I realize that this is a fairly common problem and I've found some pages that should help ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)), but all the possibilities thez show there dont wokr for me.

So first i did this:

```
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 

```

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
```
```
grub> root (hd0,5)
root (hd0,5)
```

```
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

**Error 22: No such partition**

```

and this is were I got stuck, im pretty sure i did everything correct ...

so then i tried to override the windows bootloader:

```
root@ubuntu:~# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11664    93691048+   7  HPFS/NTFS
/dev/sda2           11665       23166    92389815    5  Extended
/dev/sda3           22794       23166     2996122+  82  Linux swap / Solaris
/dev/sda4           23167       24321     9277537+   c  W95 FAT32 (LBA)
/dev/sda5           11665       22792    89385597   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd17c64ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2            3825       60801   457667752+   f  W95 Ext'd (LBA)
/dev/sdb5            3825       60801   457667721    7  HPFS/NTFS


```
```
root@ubuntu:~# mkdir /mnt/root
```
```
root@ubuntu:~# mount -t ext3 /dev/sda5 /mnt/root

```
```
root@ubuntu:~# ls /mnt/root
bin    dev   initrd.img      lib32       media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lib64       mnt    root  sys  var
cdrom  home  lib             lost+found  opt    sbin  tmp  vmlinuz

```
```
root@ubuntu:~# sudo grub-install --root-directory=/mnt/root /dev/sda
**The file /mnt/root/boot/grub/stage1 not read correctly**.

```
```
root@ubuntu:~# sudo grub-install --root-directory=/mnt/root /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.
**The file /mnt/root/boot/grub/stage1 not read correctly**.

```

So this didnt work either, anzone know what I did wrong?


Thank your for your help

---

### Post by Titan8990 on 2009-01-05
Try this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by chaosdesigner on 2009-01-05
That guid is basicly the same as the things i tried, i did all those things again just to make sure but i get the same errors

---

### Post by logos34 on 2009-01-05
You need to clean up the partition table ('omitting empty partition (5)' error) before grub install will work properly

sudo sfdisk -d /dev/sda

Run the commands listed here:

[http://ubuntuforums.org/showthread.php?t=1026754&page=2](http://ubuntuforums.org/showthread.php?t=1026754&page=2)
(post #15 onwards)

[http://ubuntuforums.org/showthread.php?t=1006079](http://ubuntuforums.org/showthread.php?t=1006079)

---

### Post by Titan8990 on 2009-01-05
You used grub-install while that guide just uses grub. Give it a shot...

---

### Post by caljohnsmith on 2009-01-05
> **chaosdesigner said:**
> 

```
root@ubuntu:~# fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11664    93691048+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda2           11665       23166[/COLOR]    92389815    5  Extended
[COLOR="Red"]/dev/sda3           22794       23166[/COLOR]     2996122+  82  Linux swap / Solaris
/dev/sda4           23167       24321     9277537+   c  W95 FAT32 (LBA)
/dev/sda5           11665       22792    89385597   83  Linux

```

Any time fdisk reports "omitting empty partition(X)", that's usually a sure sign that your partition table is corrupted; that's also confirmed by the fact that the sda3 primary partition is inside of your extended partition, so it should be a logical partition instead. So unfortunately you do have a corrupted partition table, and that's most likely why Grub is giving you problems. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
And we can work from there if you want.

---

### Post by chaosdesigner on 2009-01-05
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   187382159    93691048+   7  HPFS/NTFS
/dev/sda2       187382160   372161789    92389815    5  Extended
/dev/sda3       366169545   372161789     2996122+  82  Linux swap / Solaris
/dev/sda4       372161790   390716864     9277537+   c  W95 FAT32 (LBA)
/dev/sda5       187382286   366153479    89385597   83  Linux

```

```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=187382097, Id= 7, bootable
/dev/sda2 : start=187382160, size=184779630, Id= 5
/dev/sda3 : start=366169545, size=  5992245, Id=82
/dev/sda4 : start=372161790, size= 18555075, Id= c
/dev/sda5 : start=187382286, size=178771194, Id=83

```

@logos34

I did clean it up but then 'omitting empty partition (5)' just came again

---

### Post by caljohnsmith on 2009-01-05
OK, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output including some warnings, so you don't need to be alarmed, but please post the output. Next reboot your Live CD, and when you get back into Ubuntu, please post:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
Next try:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And please post the output. If the Grub commands complete successfully, reboot, and let us know what happens. We can work from there.

---

### Post by chaosdesigner on 2009-01-05
```
ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  11663   11664-  93691048+   7  HPFS/NTFS
/dev/sda2      11664   23165   11502   92389815    5  Extended
/dev/sda3      22793   23165     373    2996122+  82  Linux swap / Solaris
/dev/sda4      23166   24320    1155    9277537+   c  W95 FAT32 (LBA)
/dev/sda5      11664+  22791   11128-  89385597   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 187382159  187382097   7  HPFS/NTFS
/dev/sda2     187382160 372161789  184779630   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4     372161790 390716864   18555075   c  W95 FAT32 (LBA)
/dev/sda5     187382286 366153479  178771194  83  Linux
/dev/sda6     366169545 372161789    5992245  82  Linux swap / Solaris
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

Im rebooting my system now so i will edit the other stuff in a few minutes.


EDIT:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   187382159    93691048+   7  HPFS/NTFS
/dev/sda2       187382160   372161789    92389815    5  Extended
/dev/sda4       372161790   390716864     9277537+   c  W95 FAT32 (LBA)
/dev/sda5       187382286   366153479    89385597   83  Linux
/dev/sda6       366169545   372161789     2996122+  82  Linux swap / Solaris
```

```

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=187382097, Id= 7, bootable
/dev/sda2 : start=187382160, size=184779630, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=372161790, size= 18555075, Id= c
/dev/sda5 : start=187382286, size=178771194, Id=83
/dev/sda6 : start=366169545, size=  5992245, Id=82
```
```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit

```

I havent tried but it seems like the problem was fixed, I will go trz it now but i guess its ovious that it worked.

Thank you very much!

Oh and could you maybe do me the favour and briefly explain me what exactly i did?


EDIT 2:

The problem is fixed and everything works perfekt again, thank you again.

---

### Post by caljohnsmith on 2009-01-05
I'm really glad to hear Ubuntu is booting OK again. :) To explain what we did with your partition table, first consider your original partition table:
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   187382159    93691048+   7  HPFS/NTFS
[COLOR="Blue"]/dev/sda2       187382160   372161789[/COLOR]    92389815    5  Extended
[COLOR="Blue"]/dev/sda3       366169545   372161789[/COLOR]     2996122+  82  Linux swap / Solaris
/dev/sda4       372161790   390716864     9277537+   c  W95 FAT32 (LBA)
/dev/sda5       187382286   366153479    89385597   83  Linux
```
Note that primary partition sda3 starts at a point that is inside of the sda2 extended partition, because the starting sector of sda3 is 366169545 which is between the start/stop points of sda2 (start=187382160 stop=372161789). sda1, sda2, sda3 and sda4 are always primary partitions (or one can be an extended partition), and sda5 upwards are the logical partitions. Also note that the sda3 partition starts well past the end of the sda5 partition, and any logical partition must have at least one available sector between its starting point and the ending point of the previous logical partition in order to accomodate the EBR (Extended Boot Record) sector that goes before that logical partition. In practice the difference between logical partitions is almost always at least 64 sectors so that they start and stop on a HDD track and not just an arbitrary sector number. And the last clue that sda3 should be a logical partition was that sda3's ending sector is exactly the same as the end of the sda2 extended partition. 

The bottom line is that everything seemed to indicate that sda3 should actually be a logical partition instead of a primary partition. So all I did was copy/paste your sda3 partition into logical partition sda6 in the partition table map that sfdisk outputs, and then make sda3 an unused partition by making its start, size, and id numbers all zero:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=187382097, Id= 7, bootable
/dev/sda2 : start=187382160, size=184779630, Id= 5
[COLOR="Blue"]/dev/sda3 : start=        0, size=        0, Id= 0[/COLOR]
/dev/sda4 : start=372161790, size= 18555075, Id= c
/dev/sda5 : start=187382286, size=178771194, Id=83
[COLOR="Blue"]/dev/sda6 : start=366169545, size=  5992245, Id=82[/COLOR]
```
Then you ran the sfdisk command to rewrite your partition table with the above values; that's an easy way of turning your sda3 partition into a logical partition, because the sda2 extended partition all ready had the correct start/stop points to accommodate the new sda6 logical partition. Anyway, that was probably more of an explanation than you wanted, but cheers and have fun with Ubuntu. :)

---

### Post by chaosdesigner on 2009-01-05
No thank you alot, that was exactly what I wanted. I always wanna make sure I learn alot out of my errors and problems, and i think i did out of this one.

---

