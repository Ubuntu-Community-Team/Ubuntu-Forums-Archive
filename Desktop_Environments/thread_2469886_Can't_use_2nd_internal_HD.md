---
title: "Can't use 2nd internal HD"
date: 2021-12-12
forum: Desktop Environments
---

### Post by Autodave on 2021-12-12
Just installed 20.04 and I cannot read or write to the 2nd internal HD.  How do I get access to this drive?

I searched the forums, but I only found one from 2006 posted.

---

### Post by grahammechanical on 2021-12-12
Does this second internal hard drive have a partition table and file system such as Ext4? Has it been partitioned? What do you see when you run the Disks utility?

Regards

---

### Post by Autodave on 2021-12-12
Formatted ext4 with one partition taking up the entire drive.

I don't know what you are asking about Disks utility.  Is this something that I need to install?

---

### Post by SeijiSensei on 2021-12-12
Try mounting it manually from the command prompt and see what results you get:

```
sudo mount -vv /dev/sdb1 /some/mountpoint
```

/dev/sdb1 usually refers to the first partition on the second hard drive.  If that's not correct for you, replace /dev/sdb1 with whatever specifies the partition you want to mount.

---

### Post by oldfred on 2021-12-12
You have to create your own mount point.
Some prefer / , /media or in your /home. I use /mnt.

#if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data
#where sdb1 needs to be your drive, partition
sudo chmod -R a+rwX,o-rwx /mnt/data
sudo chown -R $USER:$USER /mnt/data

For internal drives, I prefer to add an entry to fstab. Often better to copy an entry & adjust for your UUID & mount point.
Disks uses a default set of mount parameters that often is not the best.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Autodave on 2021-12-12
Thanks to ALL of you for your replies.  The bottom line is this: this retired guy forgot to wake his brain up before doing this and he has NO idea whatsoever why ext4 was chosen.  This drive is used only for storage, so NTFS is what it should have been formatted to.  Unfortunately, like I already said, I just wasn't thinking.  You would think that after doing this a *few* times in the last 12 years.......

Thanks again to you all!

---

### Post by oldfred on 2021-12-12
Only use NTFS if dual booting with Windows.
Linux cannot fix NTFS. It has no tools to run chkdsk nor defrag.

---

