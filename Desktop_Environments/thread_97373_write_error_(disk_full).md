---
title: "write error (disk full?)"
date: 2005-11-30
forum: Desktop Environments
---

### Post by slava on 2005-11-30
my system monitor says i have 300 megs free space in /home but when  try to copy a file to Desktop i get "write error (disk full?)" nautilus also says i have 0 free space in /home
mount:
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-8-386/volatile type tmpfs (rw,mode=0755)
/dev/hda4 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

dmesg shows no problems with /dev/hda4

any ideas please or the world will end

---

### Post by amohanty on 2005-12-01
post the output of:
df


AM

---

