---
title: "Mount External HDD on boot"
date: 2009-03-15
forum: General Help
---

### Post by brentk on 2009-03-15
I'm using kubuntu 8.10 with KDE 4.2 and my external harddrives do not mount until I open dolphin and click on each drive. I've tried playing with mount manager, gnome volme manager, every disk management utility found in package managers. Here's the hand written fstab I've tried. This actually prevents even being able to mount the drives by clicking on them as they are all 'already present in fstab' If that's the case why aren't they loading?

```
proc                /proc           proc     defaults               0       0

UUID=cccc77df-c673-489e-b523-280e457a0dd0 /               ext3     relatime,errors=remount-ro       0       1

UUID=2e249dd4-c19a-460a-858a-87afbfeba2f5  none            swap     sw         0       0

/dev/scd0           /media/cdrom0   udf,iso9660  user,noauto,exec,utf8        0       0

UUID=2278A89B78A86F6B    /media/Docs ntfs-3g  atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,iocharset=iso8859-1,codepage=437,gid=0,uid=0    0 0

UUID=1BC3-0ACA     /media/Movies vfat  atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,iocharset=iso8859-1,codepage=437,gid=0,uid=0    0 0

UUID=4A25-7B24     /media/TV vfat  atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,iocharset=iso8859-1,codepage=437,gid=0,uid=0    0 0

UUID=9ECB-CF82     /media/Music vfat  atime,suid,mand,nouser,auto,rw,dev,exec,async,umask=777,fmask=777,dmask=666,iocharset=iso8859-1,codepage=437,gid=0,uid=0    0 0

```

---

