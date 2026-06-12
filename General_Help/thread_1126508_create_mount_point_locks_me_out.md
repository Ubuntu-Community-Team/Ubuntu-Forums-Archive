---
title: "create mount point locks me out"
date: 2009-04-15
forum: General Help
---

### Post by lordgafal on 2009-04-15
ok so i followed another [post]("http://ubuntuforums.org/showthread.php?t=536390") on how to create permanent mount point (kinda got tired of mounting my drives every time i reboot)

so i did

```

uberbob@uberbob-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc2            149984704  17145324 125220556  13% /
tmpfs                  1017040         0   1017040   0% /lib/init/rw
varrun                 1017040       340   1016700   1% /var/run
varlock                1017040         0   1017040   0% /var/lock
udev                   1017040       172   1016868   1% /dev
tmpfs                  1017040       388   1016652   1% /dev/shm
lrm                    1017040      2760   1014280   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdd1            480719056 456257220     42636 100% /media/zic
/dev/sdb1            240362656 104163388 123989468  46% /media/temp
/dev/sda1            384578164 229461476 135581248  63% /media/video

```

```

sudo gedit /etc/fstab

```

added

```

/dev/sdd1 /media/zic ext4 defaults 0 0
/dev/sdb1 /media/temp ext4 defaults 0 0
/dev/sda1 /media/video ext4 defaults 0 0

```

and when i reboot my drives arrent mounted and when i try to mount them it tells me i dont have permission to do so

o and i deleted the line to mount them manually ....

heres my /etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=dae8a95b-4a6b-4030-9725-1716576f4904 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=075efb0a-291f-49e1-958b-8af365693b97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

thx so much for helping me out

---

### Post by lordgafal on 2009-04-16
please sum1 help me : )

---

### Post by adult swim on 2009-04-16
these
```
/dev/sdd1 /media/zic ext4 defaults 0 0
/dev/sdb1 /media/temp ext4 defaults 0 0
/dev/sda1 /media/video ext4 defaults 0 0
```
should be in your fstab.  they are not there in the fstab that you provided.  did you save it when you added them the first time?
also make sure that you have created the folders that you are mounting to
```
sudo mkdir /media/{zic,temp,video}
```

you might as well own the drives once they are mounted
```
sudo chown -R username /media/{zic,temp,video}
``` changing username to your user name

---

### Post by lordgafal on 2009-04-18
last time i didnt create the directories let me make em and the changes and reboot and ill repost thx

---

### Post by cariboo on 2009-04-18
Why reboot? In an Applications-->Accessories-->Terminal type:

```
sudo mount -a
```

this also has the benefit of printing out any error messages. The above command mounts all the drives that are in /etc/fstab

Jim

---

### Post by lordgafal on 2009-04-25
thanks alot worked great

---

