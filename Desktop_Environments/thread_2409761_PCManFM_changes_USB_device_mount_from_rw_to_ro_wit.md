---
title: "PCManFM changes USB device mount from rw to ro without (apparent) reason"
date: 2019-01-06
forum: Desktop Environments
---

### Post by barbudor on 2019-01-06
Hello

I have a strange behavior with PCManFM on Lubuntu 18.04

I have a USB device which nicely automount as rw :
```
/dev/sdb1 on /media/jeanmichel/CIRCUITPY type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

I can R/W to the device from term without any issue.
But as soon I point PCManFM to CIRCUITPY, it changes it to RO (I even did nothing, just shown CIRCUITPY folder in PCManFM....

```
/dev/sdb1 on /media/jeanmichel/CIRCUITPY type vfat (ro,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

It was all working fine for the last few days until I made some tests with the device forcing it to appear as RO (there is a switch on it to write-protect).
It was able to change the device switch from RO to RW mode back and forth a few time and it was working well until now.

Could PCManFM has somehow "learnt" the device in RO mode and now is always changing it to this ?

Thanks

Barbudor

---

### Post by barbudor on 2019-01-06
Hi

So far, a low level reformatting of the device seems to have solved the issue.

Thanks

---

