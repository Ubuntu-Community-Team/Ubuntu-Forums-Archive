---
title: "read-only VFAT partition problems"
date: 2005-12-09
forum: General Help
---

### Post by mushr00m on 2005-12-09
My system has been acting odd lately and has culminated with a complete failure of write capabilities on VFAT mounts on my SATA harddrive.  Not much has changed of late on the system, but I have recently installed vmware.

I wish I just had more insight into the problem....

Questions:
1. my first question is where else I could find system info directing me to the offending app?

2. how can I fix this?
my fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#custom drives
/dev/sda5	/media/dock	vfat	umask=000	0	0
/dev/sda6	/media/warehouse	vfat	umask=000	0	0

/dev/sda1	/media/windows	ntfs	umask=0222	0	0

#bound dirs
none /tmp/jack tmpfs defaults 0 0


#/home/rkosborne/installdir/jre1.5.0_04	/usr/lib/java	none	bind
#/media/dock/downloads	/home/xxxxxxxx/Desktop/Downloads	none	bind

```
mount output:
```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda5 on /media/dock type vfat (rw,umask=000)
/dev/sda6 on /media/warehouse type vfat (rw,umask=000)
/dev/sda1 on /media/windows type ntfs (rw,umask=0222)
none on /tmp/jack type tmpfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by frodon on 2005-12-09
You could try to modify your fstab line like that : ```
/dev/sda5	/media/dock	vfat	iocharset=utf8,rw,user,exec,umask=000	0	0
```Then do a "sudo mount -a" or reboot, i'm not sure it will work but you should try.

---

### Post by mushr00m on 2005-12-09
thanks that worked well.

---

### Post by mushr00m on 2005-12-09
worked not so well...

How can I tell whats got the partition locked?

Azureus is telling me:
```
Error: /media/dock/downloads/transit/xxxxxxxx.xxx (Read-only file system), open fails, flush fails when processing file 'xxxxxxxxx.xxx'
```

---

### Post by mushr00m on 2005-12-09
it seems to be a read/write problem with only a single partition, but affects all users... well at least myself and root
Identical fstab entries but the problem is limited to /dev/sda5
```

/dev/sda5	/media/dock	vfat	iocharset=utf8,rw,user,exec,umask=000	0	0
/dev/sda6	/media/warehouse	vfat	iocharset=utf8,rw,user,exec,umask=000	0	0
```

---

### Post by mushr00m on 2005-12-09
bump

---

