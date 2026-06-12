---
title: "garbled name for a mounted drive"
date: 2006-07-05
forum: Desktop Environments
---

### Post by rkakkar on 2006-07-05
when i mount this particular drive, gnome shows its name having some junk characters (see screenshot).. although:

```

/media$ ls
c_drive  cdrom  cdrom0  d_drive  e_drive  f_drive

$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/hda1 on /media/c_drive type vfat (rw,utf8,umask=007,gid=46)
/dev/hda5 on /media/d_drive type vfat (rw,utf8,umask=007,gid=46)
/dev/hda6 on /media/e_drive type vfat (rw,utf8,umask=007,gid=46)
/dev/hda7 on /media/f_drive type vfat (rw,utf8,umask=007,gid=46)


```

shows the names correctly.. (the drive whose name is messed up is e_drive).

how can i fix this? its not allowing me to renaming through nautilus.

---

### Post by crankcaller on 2006-07-05
I have a filename in my home folder that looks like that...

---

### Post by rkakkar on 2006-07-06
*bump*

---

### Post by pt123 on 2006-10-27
I have the same problem in Edgy too.

---

