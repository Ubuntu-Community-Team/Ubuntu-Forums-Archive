---
title: "Cannot automount a NTFS partition"
date: 2008-12-30
forum: Desktop Environments
---

### Post by klemencic on 2008-12-30
I am using Ubuntu 8.10 and dual booting with XP and have two HDD installed
At boot time I wish to automount two NTFS partitions, one will mount and the other wont
The partitions I wish to mount are sda1 and sda3. I can automount sda3 no problems
I using Pysdm to do this graphically 
When  I select sda1, it comes up with sdb1 and selecting sdb1, all of the settings are identical as when I selected sda1 (see attached files sda1 and sdb1)

I did dry to copy the /dev/sda3 entry and change it to sda1 in /etc/fstab but then it just gave me an error about illegal options and wond't let me mount the partition at all

My /etc/fstab file is as follows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                              0  0  
# /dev/sda7
UUID=a62016d5-9fa9-4383-9ac6-8a157a76065b  /              ext3         relatime,errors=remount-ro            0  1  
# /dev/sda5
UUID=394cfda2-e485-41cf-be47-f0f5556b7c5f  /home          ext3         relatime                              0  2  
# /dev/sda6
UUID=51a26800-e2ce-4e8a-9ea3-1ed9ef9e0f38  /usr           ext3         relatime                              0  2  
# /dev/sda9
UUID=d5a8f69d-4621-450e-8b74-daf3570d89bb  /virtual       ext3         relatime                              0  2  
# /dev/sda8
UUID=610a3f4c-2bb5-43ab-a479-1c70a6e1d3f0  none           swap         sw                                    0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                 0  0  
#usbfs
none                                       /proc/bus/usb  usbfs        devgid=46,devmode=664                 0  0  
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,users,noauto,umask=000  0  0  
/dev/sda2                                  /media/sda2    ext3         errors=remount-ro,users,noauto        0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                              0  0  
/dev/sda5                                  /media/sda5    vfat         users,noauto                          0  0  
/dev/sdb9                                  /media/sdb9    ext3         errors=remount-ro                     0  0  
/dev/sdb5                                  /media/sdb5    ext3         errors=remount-ro                     0  0  
/dev/sdb6                                  /media/sdb6    ext3         errors=remount-ro                     0  0  
/dev/sdb7                                  /media/sdb7    ext3         errors=remount-ro                     0  0  
/dev/sdb8                                  /media/sdb8    swap         sw                                    0  0  

can anyone see the problem and help me with a solution

---

