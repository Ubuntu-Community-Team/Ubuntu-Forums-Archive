---
title: "Error 13 at GRUB menu"
date: 2009-03-26
forum: General Help
---

### Post by solidsnake76 on 2009-03-26
I've partitioned my hd into an XP partition and an Ubuntu one. When in ubuntu i was moving a file to what i thought was an external harddrive (but now i think is a partition of my main harddrive) but i think i copied the file to the partition instead of to the folder that i mounted the partition to.

So i put: sudo cp *file* /dev/sda2 instead of 
          cp *file* /mnt/sda2


Now when I get to the boot menu and try to boot Windows XP i get this error

Error 13: Invalid or unsupported executable format

When i look at my partitions under fdisk I still see an NTFS partition under /dev/sda2 but I can't mount it. It says 'NTFS Signature is missing'. If anyone could help on this it would be greatly appreciated, because im plumb out of ideas on how to solve the problem.

---

### Post by solidsnake76 on 2009-03-26
bump

---

### Post by solidsnake76 on 2009-03-27
Can anyone help me out?

---

### Post by meierfra. on 2009-03-28
> i was moving a file 

 What was  the size of that file?

If it wasn't  too large one might be able to rescue the partition:


[SIZE="3"][COLOR="Red"]Boot into Ubuntu[/COLOR][/SIZE]

**Step 1 Fix the Boot Parameter Block of your Windows Partition**

 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select  your Windows partition and choose
"boot"
"BackupBS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk. 


[SIZE="3"][COLOR="Red"]Boot from your Windows CD[/COLOR][/SIZE]

and press "r" to get  to the repair console

**Step 2 Fix the Bootsector**

Type
```
 map 
```
to determine the drive letter of your windows partition. Then 
type

```
fixboot C:
```
(but replace "C:" by  drive letter of your windows partition.

**Step 3 Run  a file system check**

Still in the Repair console of the Windows CD:

```
chkdsk /r C:
```
again use the drive letter of your Windows partition.

Run "chkdsk /r C:" as often as it takes, that is until it does not find any more errors.


If you have valuable Data on the XP partition, which is not backup up, I suggest that you clone your XP partition before you attempt any of this.

---

