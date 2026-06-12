---
title: "rw error"
date: 2006-09-07
forum: Desktop Environments
---

### Post by sparks40 on 2006-09-07
When I issue the "mount" command I get the following results:

/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)

Fhe first line seems to indicate that there are rw errors on my root partition and it has been rendered to ro. How can I correct this condition?

TNX

---

