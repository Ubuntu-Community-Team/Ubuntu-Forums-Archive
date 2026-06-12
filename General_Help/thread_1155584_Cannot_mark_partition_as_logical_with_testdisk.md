---
title: "Cannot mark partition as logical with testdisk"
date: 2009-05-10
forum: General Help
---

### Post by zorkerz on 2009-05-10
Ok Ill try to quickly explain my situation. My hardrive has an extended partition with 3 logical partitions inside; an ext4 partition with the jaunty install, an ext3 partition with my home directory, and a SWAP partition.

Yesterday I installed XP on part of the free space infront of the extended partition. Later I noticed that gparted reported the whole drive as unnallocated space even though I could use all partitions including boot into Ubuntu and XP. 

I installed testdisk (6.11.3 becauses older versions do not support ext4). It reports "Warning: incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)" although this does not appear to be a show stopper. Then I was stupid and tried to fix this by incorrectly writing over the partition with testdisk rendering both Ubuntu and XP unbootable.

So im running on a live cd (livd usb broke). After doing a deep search with testdisk it finds all the correct partitions (a few incorrect ones) and I can see the files within them, however, it will not allow the ext3 data partition to be marked L (logical). It also says in red "structure: bad." if I try to mark as P (primary) or * (primary bootable).

Ive attached a screenshot with the partition that should be marked logical highlighted.

Anybody know why it can't be marked logical or how else I can fix it?

---

### Post by zorkerz on 2009-05-11
Its not particularly important to me that the partition be maintained but I would prefer not to lose the data on it. Unfortunately I don't currently have access to a spare 65+GiB to copy it all over to. 

As I said before testdisk recognizes all my files. I guess today I'm going to try and learn about ways to copy at least part of the data somewhere else.

If anyone has some ideas or suggestions they would be much appreciated. thanks

---

### Post by unutbu on 2009-05-11
The error you are receiving from testdisk is new to me, so I don't know for sure if the following will work. However, perhaps it is worth a try: 

Boot from the LiveCD. Open a terminal and type
```

sudo sfdisk -d /dev/sda > partition_table.txt
```

Then post partition_table.txt as an attachment here. 
To make things utterly clear, please also indicate which lines in the "Deeper Search" output from testdisk correspond to the partitions you wish to keep.

I will then edit the partition_table.txt, and post the modified version. We will then use sfdisk to modify your partition table.

To give you an idea of how this works: See for example,

[http://ubuntuforums.org/showpost.php?p=6663919&postcount=716](http://ubuntuforums.org/showpost.php?p=6663919&postcount=716)
[http://ubuntuforums.org/showpost.php?p=7103244&postcount=847](http://ubuntuforums.org/showpost.php?p=7103244&postcount=847)

---

### Post by zorkerz on 2009-05-11
ok partition_table.txt is attached. sfdisk output to the terminal the following 
> Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently. At some point in the future I need to figure out why installing tinyXP messed around with the heads/cylinder count I think this warning is related to that.

I used photorec today and it recovered 1.2 gig of data although not the one file I would really like. To store this I created an ext2 partition in the remaining unpartitioned space between the tinyXP and extended partitions. I don't think this has any meaningful effect for us anyway my partition_table.txt was created afterword. Point being my partition table has changed slighlty so I have attached another screenshot.

Deeper search testdisk lines to keep (others have been removed)
* HPFS - NTFS              0   1  1  1305 254 63   20980827 [tinyXP]
P Linux                 1306   0  1  2464 254 63   18619335
L Linux                 2465   2  1  3123 254 63   10586709 [/ekg]
D Linux                 3125   0  1 11638 254 63  136777410 [home]
L Linux Swap           11639   1  1 12160 254 63    8385867

-keep all the green lines and [home] or remove all the deleted lines except [home].
-In terms of important data [home] is the only important partition assuming testdisk is correctly labeling the boundaries which strongly appears to be the case.

Judging from the sizes in partition_table.txt sda2 and sda4 should be removed and a new one needs to be added for [home] but I'm just guessing around here without any experience.

Thank ya so much.

---

### Post by unutbu on 2009-05-11
Boot from the LiveCD.
Save the attached file new_partition_table.txt to the Desktop.
Open a terminal and type
```

ls -l ~/Desktop/new_partition_table.txt
```

to make sure the file is in the right place.
If it returns
```

-rw-r--r-- 1 cyrano cyrano 412 2009-05-11 17:22 /home/zerkerz/Desktop/new_partition_table.txt
```

then proceed with
```

sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/partition_table.save < ~/Desktop/new_partition_table.txt
```

Hopefully you have not changed the partition table since your last post. If you have,
make sure you save ~/Desktop/partition_table.save to a USB Flash key.

Take a look at the new partition table with
```

sudo fdisk -l
```

See if you can mount home:
```

sudo partprobe
sudo mount /dev/sda7 /mnt
```

If all went well, home should now be mounted at /mnt

---

### Post by unutbu on 2009-05-11
zorkerz, the original new_partition_table.txt that I posted had a slight error in it which might upset sfdisk. 

If you encounter a problem, please re-download new_partition_table.txt
from the post above and try again.

---

### Post by zorkerz on 2009-05-15
Sorry its taken me so long to check back in. In short mission success!

I followed your instructions using the first new_partition_table.txt. I did receive some errors along the way which I have attached if anyone is interested in seeing them. I was unable to mount my home partition without rebooting. Also somehow the ubuntu install on my usb key (that I have been using) was messed up in the process  returning a grub error 15 when I tried to reboot from it. With a live CD, however, I was able to mount all of the partitions on my hardrive. I then reinstalled grub and needed to run fsck on the home partition before being able to successfully boot. fsck did find a few errors on the home partition but that is to be expected after what I have put it through in the last few days. Only loss I have noticed is everything that was stored on my desktop which fsck found a problem with. 

Thank you so much for your help. I would not have known what to do without it.

If I can figure out how I will mark this as solved.

cheers

---

### Post by unutbu on 2009-05-16
zorkerz, thanks for reporting back on how you solved the problem. 
I'm glad the sfdisk command produced a partition table which allowed you to proceed with recovering your home partition!

Thanks also for including the terminal output, errors.txt. 

To mark the thread as solved, edit the title of your first post.

---

### Post by Lord_JABA on 2011-01-12
I have very similar problem. After installing customized xp my data partition  disappear.
This is what i have now:
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1   764 254 63   12289662
 2 P Linux                  765   0  1  1654 254 63   14297850
 3 P HPFS - NTFS           1655   0  1  2148 254 63    7936110
 4 E extended LBA          2149   0  1 19456 254 63  278053020
   X extended              2149   0  2  2233 254 63    1365524 
 5 L Linux Swap            2149   2  1  2233 254 63    1365399

```there shold be one more logical ntfs  partition at the and of disk


Results of  testdisk quick search are OK(im sure cause i recover some files):
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1   764 254 63   12289662
D Linux                  765   0  1  1654 254 63   14297850
D HPFS - NTFS           1655   0  1  2148 254 63    7936110
D Linux Swap            2149   2  1  2233 254 63    1365399
D HPFS - NTFS           2234   0  1 19456 254 63  276687495 [Wszystko]
```But i can't mark last partition as logical.
To be very clear i wanted it to look like this: (This how it probably looked before i messed up)
```
 1 * HPFS - NTFS              0   1  1   764 254 63   12289662
 2 P Linux                  765   0  1  1654 254 63   14297850
 3 P HPFS - NTFS           1655   0  1  2148 254 63    7936110
 4 E extended LBA          2149   0  1 19456 254 63  278053020
   X extended              2149   0  2  2233 254 63    1365524 
 5 L Linux Swap            2149   2  1  2233 254 63    1365399
 6 L HPFS - NTFS           2234   0  1 19456 254 63  276687495 [Wszystko]

```detailed scan results is a mess cause i migrate from smaller disk few months ago:
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1   764 254 63   12289662
P Linux                  765   0  1  1654 254 63   14297850
D HPFS - NTFS           1655   0  1  2148 254 63    7936110
D HPFS - NTFS           1738   0  1  7295 254 63   89289270 [Wszystko]
D Linux Swap            2149   2  1  2233 254 63    1365399
D HPFS - NTFS           2234   0  1 19456 254 63  276687495 [Wszystko]
D HPFS - NTFS           2234   0 15 19456 254 63  276687481

```[B]If it is possible i like to avoid touching working partitions(if UUID's change it will mean extra work for me)

And of course if the other way is better for this i don't need to do this with testdisk.

[/B]
PS i tried to figure it out myself but i have no idea how do you calculate "start=" value. only Size values are the same
and rest make no sense to me.

---

