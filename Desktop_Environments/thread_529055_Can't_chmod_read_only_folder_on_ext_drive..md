---
title: "Can't chmod read only folder on ext drive."
date: 2007-08-18
forum: Desktop Environments
---

### Post by SyCo123 on 2007-08-18
I have an 250Gb  external USB drive. I can write files to it no problem however one of the folders is read only and i can't  delete it. 

tried
PWD
/media/New Volume

simon@ubuntu:/media/New Volume$ ls -oh
total 4.0G
dr-xr-xr-x 1 root 100K 2007-02-15 17:54 data
dr-xr-xr-x 1 root 8.0K 2007-04-29 20:37 Desktop Items
dr-xr-xr-x 1 root  24K 2007-04-29 12:56 Dieu' Documents
dr-xr-xr-x 1 root 4.0K 2007-06-12 17:40 downloads
dr-xr-xr-x 1 root 8.0K 2007-08-17 18:26 From CDs
dr-xr-xr-x 1 root  36K 2007-06-13 22:33 getDatabkRecovery
-r-xr-xr-x 2 root 4.0G 2007-02-08 18:45 kubuntu-6.10-dvd-i386.iso
dr-xr-xr-x 1 root 4.0K 2007-08-17 12:43 My Pictures
dr-xr-xr-x 1 root  24K 2007-02-15 16:59 recovered
dr-xr-xr-x 1 root    0 2007-02-13 14:58 RECYCLER
dr-xr-xr-x 1 root 4.0K 2007-02-13 13:32 System Volume Information
dr-xr-xr-x 1 root    0 2007-01-30 09:18 $VAULT$.AVG


the folder 'data' is about 80Gb of recovered data from another crashed drive and I can browse the data fine in Linux but in windows it reads 0 bytes..


simon@ubuntu:/media/New Volume$ sudo chmod 777 data
chmod: changing permissions of `data': Read-only file system

simon@ubuntu:/media/New Volume$ ls -oh
total 4.0G
dr-xr-xr-x 1 root 100K 2007-02-15 17:54 data
dr-xr-xr-x 1 root 8.0K 2007-04-29 20:37 Desktop Items
dr-xr-xr-x 1 root  24K 2007-04-29 12:56 Dieu' Documents
dr-xr-xr-x 1 root 4.0K 2007-06-12 17:40 downloads
dr-xr-xr-x 1 root 8.0K 2007-08-17 18:26 From CDs
dr-xr-xr-x 1 root  36K 2007-06-13 22:33 getDatabkRecovery
-r-xr-xr-x 2 root 4.0G 2007-02-08 18:45 kubuntu-6.10-dvd-i386.iso
dr-xr-xr-x 1 root 4.0K 2007-08-17 12:43 My Pictures
dr-xr-xr-x 1 root  24K 2007-02-15 16:59 recovered
dr-xr-xr-x 1 root    0 2007-02-13 14:58 RECYCLER
dr-xr-xr-x 1 root 4.0K 2007-02-13 13:32 System Volume Information
dr-xr-xr-x 1 root    0 2007-01-30 09:18 $VAULT$.AVG


How can I delete this folder and get my 80Gb back?

---

### Post by taurus on 2007-08-18
How did you mount your 250GB external harddrive?  Did you use ntfs or ntfs-3g driver?  You need to use ntfs-3g driver if you want to write and delete stuff from it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by SyCo123 on 2007-11-06
I hate to say but I ended up booting back into windows and was able to delete it. 
Sorry, lol

---

