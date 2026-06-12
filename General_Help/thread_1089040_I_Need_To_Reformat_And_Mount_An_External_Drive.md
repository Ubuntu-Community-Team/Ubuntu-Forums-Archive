---
title: "I Need To Reformat And Mount An External Drive"
date: 2009-03-06
forum: General Help
---

### Post by magearwig on 2009-03-06
I bought a ROCK 500GB external drive.

It came out of the box formatted NTFS, so I reformatted it using GParted.

I seems I've sucessfully created a 465GB fat3 drive.  I still can't mount it, or even see it outside of GParted.

I feel like I'm going in circles now.  Any ideas?

---

### Post by kanikilu on 2009-03-06
Can you post the result of ```
sudo fdisk -l
```

---

### Post by magearwig on 2009-03-06
magearwig@magearwig-desktop:~$ sudo fdisk -l
[sudo] password for magearwig:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003602b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4689    37664361   83  Linux
/dev/sda2            4690        4865     1413720    5  Extended
/dev/sda5            4690        4865     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d5c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14219   114214086   83  Linux
/dev/sdb2           14220       14593     3004155    5  Extended
/dev/sdb5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0dcbcb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    5  Extended
/dev/sdc5               1       60801   488383969+  83  Linux
magearwig@magearwig-desktop:~$

---

### Post by kanikilu on 2009-03-06
Ok, so is that it, the one recognized as /dev/sdc? Or do you have another 500GB device in or connected to the computer?

Can you also post the result of **mount** from the command line?

// Edit - Oh, nevermind, that's a Linux partition, you said it was formatted as FAT32, right?

If that's not the right device, then try unplugging the external drive and then plug it back in. After doing so, copy the output of the following command: ```
dmesg | tail -n 20
```

---

### Post by magearwig on 2009-03-06
I'm sorry ext3, not fat 32.  There's only one 500GB drive.

I want to run something like sudo mount /dev/sdc/

Here's the results

magearwig@magearwig-desktop:~$ sudo mount /dev/sdc/
[sudo] password for magearwig:
mount: can't find /dev/sdc/ in /etc/fstab or /etc/mtab
magearwig@magearwig-desktop:~$

---

### Post by ponyexpress on 2009-03-06
you need to format the drive. You only partitioned it with gparted.
In order to make the file system you need to:
sudo mkfs.ext3 /dev/sdc5

---

### Post by magearwig on 2009-03-06
magearwig@magearwig-desktop:~$ sudo mkfs.ext3 /dev/sdc5
[sudo] password for magearwig:
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61063168 inodes, 122095992 blocks
6104799 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 39 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
magearwig@magearwig-desktop:~$ 

Did that, I still don't see where I can mount it, and it's still not showing up in my places menu.

magearwig@magearwig-desktop:~$ sudo mount /dev/sdc5/
[sudo] password for magearwig:
mount: can't find /dev/sdc5/ in /etc/fstab or /etc/mtab
magearwig@magearwig-desktop:~$

---

### Post by ponyexpress on 2009-03-06
gksud gedit
open /etc/fstab
add the line
/dev/sdc5 /media/sdc5     ext3    auto,user,defaults        0       2
save 

sudo mkdir /media/sdc5

mount /media/sdc5

that should mount it under /media/sdb5

---

### Post by ponyexpress on 2009-03-06
I made a typo, the first line on my previous post should be should be: 
gksudo gedit

---

### Post by magearwig on 2009-03-07
Okay.  I've got a new folder in my media folder.  
That's hot.  Now, I just gotta brush up on my chmod to get read/write privligaes.

---

