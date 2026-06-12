---
title: "cant startx, or write to /"
date: 2009-04-10
forum: General Help
---

### Post by Mr.Carramba on 2009-04-10
Hi,

After reading a bit on the net I decided to mess with fstab (not good idea)
I changed for / to noatime, nodiratime,data=writeback, error=remount
unfortunately for me after reaboot I cant startx or revert to my back up file. Since whole / is read-only.
runing mount -l shows
/dev/sda1 on / ext3 (rw, realtime, errors=remount-ro)

Which I find strange..

anyway, I m greatfull for your help getting my system back :)

Carra

---

### Post by Mr.Carramba on 2009-04-10
huh, I rebooted back to the x after remounting drive the hard way

```

mount -n -o remount -t ext3 /dev/sda1 / 

```

however, the question can be now reformulated way did these changes (noatime,nodiratime,data=writeback) messed up x? and which was it then?

---

### Post by bodhi.zazen on 2009-04-10
They did not mess up X, the partition ran into errors as it was mounted and was mouted ro.

check your options and syntax in fstab.

---

