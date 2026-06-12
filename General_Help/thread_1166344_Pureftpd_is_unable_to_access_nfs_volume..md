---
title: "Pureftpd is unable to access nfs volume."
date: 2009-05-21
forum: General Help
---

### Post by kallu_be on 2009-05-21
Pureftpd is unable to access nfs volume. Here is my fstab entry

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6c806c70-19c1-4dd4-9d58-f8fe4eb9fda5 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=2d502ca2-ae73-41c4-b793-166689e0c847 /home           ext3    relatime        0       2
# /mnt/Jupiter was on /dev/sdc1 during installation
UUID=db237c13-d27e-4975-a9ce-964f7055b0b6 /mnt/Jupiter    ext3    relatime        0       2
# /mnt/Mars was on /dev/sdb1 during installation
UUID=88f3d80e-cc79-437d-9b2c-d0b7aca28672 /mnt/Mars       ext3    relatime        0       2
# /mnt/Venus was on /dev/sda2 during installation
UUID=06C88B69C88B5639 /mnt/Venus      ntfs    defaults,umask=007,gid=46 0       1
# none was on /dev/sda7 during installation
UUID=ec723fa2-e5d9-4d7b-b655-3225806081a6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#NFS
10.129.112.132:/media/win/TV    /mnt/NFS                        nfs     ro      0       0

#for FTP
/mnt/Mars/Music                 /home/ftpusers/Music            none    bind,ro         0       0
/mnt/Mars/HD                    /home/ftpusers/Movies/HD        none    bind,ro         0       0
/mnt/Mars/Movies                /home/ftpusers/Movies/English   none    bind,ro         0       0
/mnt/Jupiter/Telugu\040Movies   /home/ftpusers/Movies/Telugu    none    bind,ro         0       0
/mnt/Jupiter/Books              /home/ftpusers/Books            none    bind,ro         0       0
/mnt/NFS                        /home/ftpusers/TV               none    bind,ro         0       0
~


```

I am getting this error

```

lftp bbuser@10.12.13.36:/> cd TV/
lftp bbuser@10.12.13.36:/TV> ls -l
ls: Access failed: 550 Can't change directory to /TV: Permission denied (-l)

```

---

