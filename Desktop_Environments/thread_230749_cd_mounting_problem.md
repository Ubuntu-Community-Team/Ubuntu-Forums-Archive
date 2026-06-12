---
title: "cd mounting problem"
date: 2006-08-06
forum: Desktop Environments
---

### Post by polloz on 2006-08-06
hello,

i have the following problem. i cannot get kubuntu mount cds or dvds properly. when i insert a cd/dvd, nothing happens, it doesnt mounts. the only way i have found i can mount a cd/dvd is when i boot the system with the disc already inserted in the drive. in that case, it loads the desktop with the cd/dvd already in it. i'm posting two images, one shows the settings i have when i boot with the cd already in the drive and the other without it. also, i'm posting what i get with fstab:

 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda2 none swap sw 0 0
/dev/sda1 /media/Windows_XP ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
/dev/scd0 /media/cdrom0 iso9660  0 0

anyone kwnos what the problem can be? thanks for your help

---

### Post by polloz on 2006-08-06
here comes the infamous *bump*

---

### Post by polloz on 2006-08-06
there goes another *bump*

---

### Post by polloz on 2006-08-07
please help *bump*

---

