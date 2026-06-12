---
title: "Windows Partition"
date: 2009-01-17
forum: General Help
---

### Post by theozzlives on 2009-01-17
hey guys/gals, is there anyway of making my Windows partition sda1 instead of sda3? I think that's why my Windows installer put Windows on F: instead of C:.

---

### Post by ajgreeny on 2009-01-17
Not without reinstalling at least one OS, as far as I am aware, and that could mean both windows and ubuntu.  I'm assuming you have both.  If you are prepared to reinstall ubuntu which is quick and easy, or if you have only just installed and have few user files on it, it could be easier to just delete your ubuntu install with gparted, move your windows partition to the front of the disk, ie sda1, and then reinstall ubuntu after ubuntu on the disk.  I know so little about windows now, that I'm not sure what moving it would do to the bootloader, and you would need to restore that with the windows install disk.  Tricky one!  Someone else may know more than me, so wait for more responses.

---

### Post by caljohnsmith on 2009-01-17
Hi theozzlives, sure, you can switch sda3 with sda1 in the partition table, so sda3 will become sda1 and vice versa. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by theozzlives on 2009-01-17
```
ozzie@ozzie-laptop:~$ sudo fdisk -lu
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux
/dev/sda2        20964825   251144144   115089660   83  Linux
/dev/sda3   *   251144145   312576704    30716280    7  HPFS/NTFS
ozzie@ozzie-laptop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83
/dev/sda2 : start= 20964825, size=230179320, Id=83
/dev/sda3 : start=251144145, size= 61432560, Id= 7, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
ozzie@ozzie-laptop:~$ 
ozzie@ozzie-laptop:~$ sudo fdisk -lu
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux
/dev/sda2        20964825   251144144   115089660   83  Linux
/dev/sda3   *   251144145   312576704    30716280    7  HPFS/NTFS
ozzie@ozzie-laptop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83
/dev/sda2 : start= 20964825, size=230179320, Id=83
/dev/sda3 : start=251144145, size= 61432560, Id= 7, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
ozzie@ozzie-laptop:~$ 
ozzie@ozzie-laptop:~$ sudo fdisk -lu
[sudo] password for ozzie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux
/dev/sda2        20964825   251144144   115089660   83  Linux
/dev/sda3   *   251144145   312576704    30716280    7  HPFS/NTFS
ozzie@ozzie-laptop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83
/dev/sda2 : start= 20964825, size=230179320, Id=83
/dev/sda3 : start=251144145, size= 61432560, Id= 7, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
ozzie@ozzie-laptop:~$ 

```

---

### Post by caljohnsmith on 2009-01-17
OK, how about first downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so that if for some reason anything were to go wrong, you can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that.

After that, boot your Live CD, and please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
Also, I'm assuming you have Grub installed to that drive, so if that is true, next do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, and it should be either (hd0,1) or (hd0,2); but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also, for whichever is your main Ubuntu partition, how about doing:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```
Please post the output of all the commands, and we can work from there.

---

### Post by theozzlives on 2009-01-17
Is there a program like Remastersys for Windows? I don't wanna lose my Trancender Activation, I don't have any left.

---

