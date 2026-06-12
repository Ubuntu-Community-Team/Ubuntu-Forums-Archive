---
title: "mount: wrong fs type, usb stick, memory cards."
date: 2008-07-04
forum: Desktop Environments
---

### Post by t_k on 2008-07-04
No matter what i plug in my laptop, i get the error: 

mount: wrong fs type, bad option, bad superblock on /dev/sda, missing 
codepage or other error In some cases useful info is found in syslog - 
try dmesg | tail or so

dmesg gives me:

[  433.245531] sd 8:0:0:0: [sdb] Write Protect is off
[  433.245536] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  433.245538] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  433.248154] sd 8:0:0:0: [sdb] 3920896 512-byte hardware sectors (2007 MB)
[  433.249525] sd 8:0:0:0: [sdb] Write Protect is off
[  433.249528] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  433.249530] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  433.249533]  sdb: sdb1
[  433.251227] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  433.251274] sd 8:0:0:0: Attached scsi generic sg2 type 0


I used to have this problem before but fixed it with this: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103)

"The problems disappears when line 155 in 
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi"

I got a clean install of kubuntu with KDE 4 Beta 2 BTW.

Help!

---

### Post by t_k on 2008-07-04
Bump

---

### Post by VMC on 2008-07-04
> **t_k said:**
> No matter what i plug in my laptop, i get the error: 

mount: wrong fs type, bad option, bad superblock on /dev/sda, missing 
codepage or other error In some cases useful info is found in syslog - 
try dmesg | tail or so

dmesg gives me:

[  433.245531] sd 8:0:0:0: [sdb] Write Protect is off
[  433.245536] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  433.245538] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  433.248154] sd 8:0:0:0: [sdb] 3920896 512-byte hardware sectors (2007 MB)
[  433.249525] sd 8:0:0:0: [sdb] Write Protect is off
[  433.249528] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  433.249530] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  433.249533]  sdb: sdb1
[  433.251227] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  433.251274] sd 8:0:0:0: Attached scsi generic sg2 type 0


I used to have this problem before but fixed it with this: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103)

"The problems disappears when line 155 in 
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi"

I got a clean install of kubuntu with KDE 4 Beta 2 BTW.

Help!

What's the output of "mount"

---

### Post by t_k on 2008-07-05
Mount gives me:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by t_k on 2008-07-09
*Bump*

---

