---
title: "accidentaly removed /etc/fstab !!! Help me before I shutdown! :)"
date: 2005-12-08
forum: General Help
---

### Post by gix on 2005-12-08
Hi all, I was installing a xen guest breezy when I've done the biggest wrong step of my sysadmin life ... 

vi /etc/fstab (guessing to write the guest fstab!!!! ... oh my god....)
100dd (deleting ALL my fstab!!!)
<copy&paste the xen guest fstab configuration>
:wq


ARGHHHHH!!!!

How can I restore my previous conf?
here's my "mount" output:

```

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hdb3 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

---

### Post by ranf on 2005-12-08
I paste mine. I already changed hdb1 and hdb3. 
For your swap partition look after it with:
```
sudo fdisk -l
```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
#fix# /dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda5       /media/win      ntfs    ro,user,noauto,umask=000        0 0
/dev/hdb3       /home               ext3    defaults,errors=remount-ro 0       1

```

---

### Post by mherring on 2005-12-08
I can't help be curious what would happen if you simply re-booted.  Not suggesting you try that.....

most of what you need is in mtab....  do "man fstab" and "man mtab" to understand the fomats.

Here is my fstab and mtab---this may help you re-create yours.

mherring@Ath:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdg1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdg5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
mherring@Ath:~$ cat /etc/mtab
/dev/hdg1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda2 /media/BACK_2 vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda1 /media/EXT_BACKUP vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/hde1 /mnt/windows ntfs rw 0 0
/dev/hdh1 /mnt/data vfat rw 0 0
mherring@Ath:~$

---

### Post by gix on 2005-12-08
Thank you guys it works!!!!

I've got help also though irc where another ubuntu-er send me his fstab (ubuntu, I love you ... :) )
I didn't touch my mtab since I've only removed (... only...) the fstab one
phewwwwwwwwww
:)

---

