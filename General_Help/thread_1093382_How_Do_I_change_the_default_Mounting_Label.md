---
title: "How Do I change the default Mounting Label??"
date: 2009-03-11
forum: General Help
---

### Post by BrandonBan6 on 2009-03-11
Hello,

I have an external HDD w/ext3 FS labeled "Backup_Drive". 

After I mount the drive, it shows up as "500.1 GB Media" (see screenshot attached) on the desktop, I want to change that to "Backup_Drive". How do I do this? 

Here's the FDISk -L entry: 
```

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1116ae0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux


```

And I mount it with the FSTAB entry:
```

#/dev/sdc1
/dev/sdc1	/media/backup_drive	ext3	

```

What do I need to do? Aside from the annoying label, everything else is running great. 

thanks a million!!

---

### Post by taurus on 2009-03-11
I think you mean label or volume name.  You can use tune2fs to change it.  Probably best to unmount it first though.

```

TUNE2FS(8)                                                          TUNE2FS(8)

NAME
       tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

SYNOPSIS
       tune2fs [ -l ] [ -c max-mount-counts ] [ -e errors-behavior ] [ -f ]  [
       -i  interval-between-checks  ]  [  -j  ]  [  -J  journal-options ] [ -m
       reserved-blocks-percentage  ]  [  -o  [^]mount-options[,...]   ]  [  -r
       reserved-blocks-count ] [ -s sparse-super-flag ] [ -u user ] [ -g group
       ] [ -C mount-count ] [ -E extended-options ] [ -L volume-name  ]  [  -M
       last-mounted-directory  ]  [  -O  [^]feature[,...]   ]  [ -T time-last-
       checked ] [ -U UUID ] device

DESCRIPTION
       tune2fs allows the  system  administrator  to  adjust  various  tunable
       filesystem parameters on Linux ext2/ext3 filesystems.


       -L volume-label
              Set  the volume label of the filesystem.  Ext2 filesystem labels
              can be at most 16 characters long;  if  volume-label  is  longer
              than  16  characters, tune2fs will truncate it and print a warn&#8208;
              ing.  The volume label can be used  by  mount(8),  fsck(8),  and
              /etc/fstab(5)  (and  possibly  others)  by specifying LABEL=vol&#8208;
              ume_label instead of a block special device name like /dev/hda5.

```

---

### Post by BrandonBan6 on 2009-03-11
Thanks Taurus, 

But it still doesn't seem to be working

I ran this: 
```

:~$ sudo umount /dev/sdc1
:~$ sudo tune2fs -L backup_drive /dev/sdc1
tune2fs 1.41.3 (12-Oct-2008)
:~$ sudo mount -l /dev/sdc1 

```

However, it still shows up as "500.1 GB Media" :(

---

### Post by taurus on 2009-03-11
Have you tried to reboot?

What's the output of this command from a terminal?

```
sudo blkid
```

---

### Post by BrandonBan6 on 2009-03-11
Oh Lame, a reboot and it works fine :redface:

Its working now :) Thank you!

---

