---
title: "firefox permission downloaded file"
date: 2012-01-18
forum: Desktop Environments
---

### Post by smashsupermario on 2012-01-18
[LEFT]Hi,
my matter is this:
I have a Nas mounted at start up with this  code:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=5fa6f7ad-3b62-447c-9d70-f8a700333d7f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=76741a42-719f-4cc7-8390-8c3252bcee78 none            swap    sw              0       0
//192.168.1.200/download /media/WDigital cifs username=<massimo>,password=<100800>,,uid=1000,gid=1000,dir_mode=0777,file_mode=0777,_netdev 0 0
//192.168.1.200/public /media/Archivio cifs username=<massimo>,password=<100800>,,uid=1000,gid=1000,dir_mode=0777,file_mode=0777,_netdev 0 0
```If I download file from firefox in a nas' folder, the file downloaded cannot be open, and the  permission are
```
-rw--w---- 1 99 massimo 1819893 2012-01-04 17:55 P52_Boll_48_2010.pdf
```If i download the same file with Chromium, i can open the file and the permission are:
Codice:
```
-rw-rw-r-- 1 99 massimo 1819893 2012-01-04 22:08 P52_Boll_48_2010 (1).pdf.crdownload
-rw--w---- 1 99 massimo 1819893 2012-01-04 17:55 P52_Boll_48_2010.pdf
```When i rename the file deleting  ".crdownload" the file can be open.
I'd like to use firefox..... Anyone can help me.
P.s. Sorry for my english.:sad:
[/LEFT]

---

