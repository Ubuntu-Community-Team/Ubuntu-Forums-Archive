---
title: "Want to Access External Hard-Drive"
date: 2009-04-12
forum: General Help
---

### Post by Th3_Tux on 2009-04-12
Hi All, I have just installed Intrepid 8.10 on my external hard-drive and now I want to access my music and movies which are located on my HD , but I can't find a way.

When I logged in windows which is on my internal HD I can access my stuff

Any help please?:guitar:

---

### Post by statistic on 2009-04-12
First create a folder in /mnt with a good name.
eg. sudo mkdir /mnt/winxp

Then you add a line to /etc/fstab that looks something like:

/dev/sda1  /mnt/winxp  ntfs-3g  defaults  0 0

So /dev/sda1 is your device, which here is the first partition on your internal harddrive is most likely is named as such. 

Then /mnt/winxp is your mount point, opening this folder from here on out will contain the contents of the mounted partition.

ntfs-3g is the file-system to use, and ntfs-3g would be used for a Windows partition.

defaults tells it to use default settings. And the "0 0" is just usually the setting you want, I forget what they do now.

Now if you want to mount it use "mount -a" to mount it right away, and it should mount itself every boot from now on.

---

