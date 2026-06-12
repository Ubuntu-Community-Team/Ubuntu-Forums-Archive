---
title: "disk usage error"
date: 2005-11-23
forum: Desktop Environments
---

### Post by whitewizardcoder on 2005-11-23
Hi,
I'm having some trouble with my /, /proc, /dev, and /sys filesystem disk usage reports.  If i'm not mistaken /proc, /dev, and /sys should be virtual filesystems.  As of recently, System Monitor reports around 0.5 GB more used space on my root filesystem than is actually being taken up (which I found out using Filelight).  /proc, /dev, and /sys both show 0 bytes for total space.  I checked the size of these manually, and it was around 0.5 GB.  This led me to believe that these filesystems are actually being mounting to the hardrive.  Is this a problem, or is it just a glitch in the disk usage software?  Also, how can this be fixed?  Any help is appreciated.

Thanks,
WhiteWizardCoder

Related information:
mount:
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type vfat (rw,noexec,nosuid,nodev,uid=1000,utf8,iochars et=utf8,umask=0000)
/dev/hda5 on /media/hda5 type vfat (rw,noexec,nosuid,nodev,uid=1000,utf8,iochars et=utf8,umask=0000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Filelight shows 2.8 GB used
System Monitor shows 3.4 GB used

---

