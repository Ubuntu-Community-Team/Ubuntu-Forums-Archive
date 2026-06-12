---
title: "Extra icons in Nautilus &quot;Places&quot; sidebar"
date: 2012-11-05
forum: Desktop Environments
---

### Post by wurlyfan on 2012-11-05
Hi. Some time ago some extra icons appeared in the Nautilus "Places" sidebar (ringed in the attached pic), which appear to represent the mount points of the volumes already listed. I don't remember what I did to make them appear (if anything). When I click on any of these icons I get a message telling me that the volume is already mounted (which it is).

I would be quite happy to use these "mount point" icons instead of the icons with the volume names, but I don't want both appearing in the Places list. I note that if I open Nautilus as root, these mount point icons are all that appear (and they are functional with no error message).

Can anyone explain what is happening here, so I can eliminate the duplication? Here is my fstab, if that helps:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / is on /dev/sda3
UUID=0fa38026-bbe8-4a44-a6d3-e5a0328f0e58 /               ext4    errors=remount-ro 0       1
# /media/DATA is on /dev/sda2
UUID=4DB2ED2A4D7DD73B /media/DATA     ntfs    defaults,user 0       0
# swap is on /dev/sda4
UUID=337d097a-cdab-447d-826e-b1c4d7274f38 none            swap    sw              0       0
# /media/TV2 is on /dev/sdb1 (2TB)
UUID=2E38C20638C1CD51 /media/TV2      ntfs    defaults,user 0       0
# /media/MEDIA1 is on /dev/sdc1 (2TB)
UUID=4549494420BBFD63 /media/MEDIA1   ntfs    defaults,user 0       0
# /media/TV1 is on /dev/sdd1 (2TB)
UUID=52C2D361C2D347BD /media/TV1      ntfs    defaults,user 0       0
# /media/ARCHIVE is on /dev/sdf1 (1T5B)
UUID=7623D8F14782266C /media/ARCHIVE     ntfs    defaults,user 0       0
# /media/SPARE is on /dev/sdh1 (1TB dock)
# UUID=535570FF5B87BC34 /media/SPARE     ntfs    defaults,user 0       0
#
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I am running Ubuntu 11.04 on an oldish i386 box (with plans to update both hardware and version soon).

Cheers!

---

### Post by mc4man on 2012-11-05
Maybe take a glance here, 2 links to check in post 2
Basically you want to edit your fstab & change the _affected _ones  from 
 UUID=xxxxx...
to 
 /dev/disk/by-uuid/xxxxx... 
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by wurlyfan on 2012-11-05
Thanks mc4man, that solved it for me as well.

---

