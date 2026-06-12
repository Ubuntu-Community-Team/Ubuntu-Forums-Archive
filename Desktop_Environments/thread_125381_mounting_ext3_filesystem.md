---
title: "mounting ext3 filesystem"
date: 2006-02-03
forum: Desktop Environments
---

### Post by endoubt on 2006-02-03
I'm running Hoary on an 8 gig drive and I had previously been running Hoary on a 60 gig that had been taken out of the computer.  Now I want to access all the data on that drive but I can't figure out how to mount the device (60gig ext3 filesystem) in the 8gig's hoary install.

From the Ubuntu guide I know how to mount a fat32 or ntfs filesystem that runs flawlessly, but I don't know the command to mount the ext3 on /dev/hdc to the directory /media/maxtor that I created.

Any help would be greatly appreciated.

~Russ
Atlanta

---

### Post by localzuk on 2006-02-03
try

```

mount -t ext3 /dev/hdc /media/maxtor

```

---

### Post by endoubt on 2006-02-06
> sudo mount -t ext3 /dev/hdc /media/maxtor
mount: /dev/hdc already mounted or /media/maxtor busy

How could I find out where /dev/hdc is mounted?  I don't know why it would say this.

Thanks,
Russ

---

### Post by drummer on 2006-02-06
```
mount
```will tell you all the file systems that are mounted.

---

### Post by endoubt on 2006-02-06
mount shows:

> /dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)


I don't see /dev/hdc anywhere

thanks,
~Russ

---

### Post by Gcool on 2006-02-06
Try ```
mount -t ext3 /dev/hdc**1** /media/maxtor
```

---

### Post by endoubt on 2006-02-07
damn, I feel like a fool, thanks, that did it

~Russ
Atlanta

---

