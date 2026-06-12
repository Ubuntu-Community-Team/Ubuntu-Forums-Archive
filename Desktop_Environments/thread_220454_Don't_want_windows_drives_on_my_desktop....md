---
title: "Don't want windows drives on my desktop..."
date: 2006-07-21
forum: Desktop Environments
---

### Post by abhiomkar on 2006-07-21
I use GNOME, i don't want windows drives on my desktop. How could i remove them from my desktop without unmounting them.

About My Disk partitions..
my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0      1
/dev/hda1     /media/hda1     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
/dev/hda5     /media/hda5     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
/dev/hda6       /media/hda6     vfat    rw,auto,user,fmask=0111,dmask=0000 0       1
/dev/hdb5     /media/hdb5     ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

my mtab:
/dev/hda8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/fuse /media/hda1 fuse rw,nosuid,nodev,noatime,default_permissions,allow_other 0 0
/dev/fuse /media/hda5 fuse rw,nosuid,nodev,noatime,default_permissions,allow_other 0 0
/dev/hda6 /media/hda6 vfat rw,noexec,nosuid,nodev,fmask=0111,dmask=0000 0 0
/dev/fuse /media/hdb5 fuse rw,nosuid,nodev,noatime,default_permissions,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

thanku

---

### Post by krismatth3 on 2006-07-21
You can prevent any volumes from being on your desktop by running "gconf-editor", browsing to /apps/nautilus/desktop, and unchecking "volumes_visible".

---

### Post by aysiu on 2006-07-21
Alternatively, you can mount them to folders outside of /media or /mnt

I mount my Windows partition to /windows

---

