---
title: "Trouble with file permissions"
date: 2009-04-25
forum: General Help
---

### Post by TheLions on 2009-04-25
Hi!

I have 6 NTFS partitions (sda1,5,6,7;sdb 5,6) which I want to be auto-mounted at start-up, also i would like to be able to unmount it directly from nautilus as user and I would like read, write and execute permissions on those partitions. 
How should I edit my /etc/fstab so i can achieve that?

Currently my fstab looks like:
**************************************************************
...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                         0  0  
# / was on /dev/sdb1 during installation
UUID=659f8d84-ad14-4ee3-93b4-cc7c73a1a36d  /               ext4         relatime,errors=remount-ro                       0  1  
# swap was on /dev/sdb3 during installation
UUID=c6594aca-eb1b-4a64-88db-c38c4c2f9f9e  none            swap         sw                                               0  0  
tmp                                        /tmp            tmpfs        defaults,noexec,mode=0777                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                            0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8                            0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                         0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0  
/dev/sda5                                  /media/sda5     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0  
/dev/sda6                                  /media/sda6     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0  
/dev/sda7                                  /media/sda7     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0  
/dev/sdb5                                  /media/sdb5     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0  
/dev/sdb6                                  /media/sdb6     ntfs         nls=iso8859-1,ro,users,umask=777,gid=users,user     0  0
******************************************************************

---

### Post by logos34 on 2009-04-25
ntfs-config should fix you up:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron))

---

### Post by TheLions on 2009-04-26
using NTFS-config doesn't allow me to unmount my partitions...:(

EDIT:
I figured out it!

here how it looks now:
[html]
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
/dev/sda5                                  /media/sda5     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
/dev/sda6                                  /media/sda6     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
/dev/sda7                                  /media/sda7     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
/dev/sdb5                                  /media/sdb5     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
/dev/sdb6                                  /media/sdb6     ntfs         nls=iso8859-1,locale=hr_HR.UTF-8,users,umask=000,gid=users,user,uid=<my_username>  0  0  
[/html]

---

