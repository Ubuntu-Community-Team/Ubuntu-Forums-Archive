---
title: "Dual boot Fat32 not writable because nautilus"
date: 2006-04-05
forum: Desktop Environments
---

### Post by wanna_ubuntu on 2006-04-05
Hi, i have a Compaq V2000 laptop with dual boot winXP and ubuntu. WinXP is on a ntfs partition, ubuntu is on a ext 3 partition. I have a third fat32 partition that i keep my work on that i can access from both (in theory). Problem is, when i try to write to it from ubuntu, it complains that the drive is not writeable. More specifically, when i first boot up, if i open a console window i can open and write files, however if i use nautilus to access the file, then it will not let me write to the drive. I suspect that when nautilus accesses the drive it is changing the settings. What can i do to fix this? Any suggestions would be greatly appreciated. 
-Matt

---

### Post by aysiu on 2006-04-05
Try these:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by wanna_ubuntu on 2006-04-06
Thank you for the links, unfortunately I have already tried what they suggested. I may be wrong, but the line is the fstab file like this:
'/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0 '
specifically 'umask=000' mounts the filesystem with all users having full access. This works as expected (without using 'sudo' i can write to the partition) **as long as i only use the console** to access the fat32 partition. If i use nautilus to access the file, it will not let me write to the partition, even if i start nautilus with root privilages.

---

