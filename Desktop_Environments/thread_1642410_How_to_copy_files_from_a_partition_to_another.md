---
title: "How to copy files from a partition to another"
date: 2010-12-10
forum: Desktop Environments
---

### Post by ldesamero on 2010-12-10
Hi All,

Now I have learned creating partition in linux (ubuntu), well that's an achievement for a newbie. 

The next thing that I want to know is, how can I *copy the contents of a partition to another partition*. Like if I want to backup its content to a new partition that Im going to create.


Any ideas please. And Thank you

---

### Post by 3Miro on 2010-12-10
If you go to Places -> Home, you will open Nautilus (the file manager) and on the left you should see a list of all the partitions on your computer. If you click on a partition, it will "mount" that partition as it will become a folder in /media/some_random_name. Then you can move files to that folder and they will be written onto the partition (you can also just click on the partition link on the left and drag/drop file on it).

---

### Post by oldfred on 2010-12-10
Not really different than moving /home. But you also should use commands that include preserving permissions & ownership.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Or these links to backups
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
See info & links on grsync & rsync

---

### Post by ldesamero on 2010-12-10
Thank you for the reply guys, that helped me.

I was just thinking if this scenario is possible:

I have an existing partition sdb1 and I created a new partition sdb2,  then copied the contents of sdb1 to sdb2. Then I deleted my sdb1  partition. Now I want my sdb2 to act as my previous sdb1 that I have  deleted so that I could mount it again from the previous directory where  the old sdb1 is mounted and use all the copied files or maybe also  applications from the previous deleted partition; and also renaming sdb2  to sdb1?

Basically the contents of sdb2 will be a total replication of what sdb1  have before, but might have a difference in size. Example: old sdb1 is  10GB, then sdb2 is 8GB. So if you could notice, sdb1 is a copy of sdb2  that is being Shrinked in size


Any ideas from all the members here if this is possible? And if yes how can this be achieved?

For some reason I preferred using native scripts of linux, like fdisk, cp, etc and not
using other apps to achieve this.


THank you very much

---

### Post by 3Miro on 2010-12-10
This depends on what you are doing. Here is a tutorial for fstab, which can be used to create permanent associations between folders and partitions.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

For example, you have /home on sdb1, then you copy that to sdb2. Then from a LiveCD, you can change the line:

UUID="something_for_sdb1" /home ext4 defaults 0 0
to
UUID="something_for_sdb2" /home ext4 defaults 0 0

To find out what the something needs to be, use:
```
 ls -al /dev/disk/by-uuid/ 
```
then you will see lines like:
```
 something_for_sdb1 -> ../../sdb1
something_for_sdb2 -> ../../sdb2 
```

Also, when you copy the content, make sure you have the right permissions for it (especially for /home or other important folders like /bin /usr ... )

---

### Post by ckop64 on 2010-12-10
If the partition isn't mounted by default, you should mount it. Create a mountpoint (eg. /media/HD2)
sudo mount -o,loop /dev/sdb1 -t ntfs-3g /media/HD2

---

