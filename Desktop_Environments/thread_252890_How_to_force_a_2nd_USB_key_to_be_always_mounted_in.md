---
title: "How to force a 2nd USB key to be always mounted in the same directory ?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by TomG on 2006-09-07
Hi,

I have two USB Keys which appear like this in the FSTAB :
/dev/sdb1	/media/usbkey1	vfat rw,user,auto,exec,gid=100,uid=1000...
/dev/sdc1	/media/usbkey2	vfat rw,user,auto,exec,gid=100,uid=1000...

My problem is that when USBKEY1 is absent, ie not plugged, the USBKEY2 becomes SDB1 (instead of SDC1) and so is mounted into /media/usbkey1.
This leads to mismatching directory versus content of the key and causes problem (backup...).

Question : How to Force a key to be mounted in a specific directory ?

Thanks for your advises,
TomG

---

### Post by TomG on 2006-09-07
bump

---

### Post by astoltz on 2006-09-07
You need a udev rule.  See this [http://www.ubuntuforums.org/showthread.php?t=168221]("http://www.ubuntuforums.org/showthread.php?t=168221")

---

### Post by TomG on 2006-09-07
Thanks Astoltz :)

---

