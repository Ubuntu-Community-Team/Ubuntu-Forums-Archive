---
title: "Is my floppy in wrong directory?"
date: 2009-04-04
forum: Desktop Environments
---

### Post by alexham on 2009-04-04
Hi,

I have been trying to make a boot floppy, but none of the terminal commands work.  I.e. mke2fs /dev/fd0 responds cannot read ----no such file---?
When I insert a floppy into the drive it does no appear on the desktop, but I can find it in Places/Home.  I have to right click and select Re-scan and then the Icon appears and its location is /media/floppy0.

I can boot from CD so this is not a matter of life or death, just curious.

Many thanks,

Alex

---

### Post by Shazaam on 2009-04-04
This should be in /etc/fstab...
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Also, have you tried this?...
```
sudo modprobe floppy 
```
And read this...
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/255651](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/255651)

---

### Post by alexham on 2009-04-04
> **Shazaam said:**
> This should be in /etc/fstab...
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Also, have you tried this?...
```
sudo modprobe floppy 
```
And read this...
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/255651](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/255651)Thank you for such instant reply. Yes the line in fstab is exactly like you wrote, but modprobe floppy does not do anything.

By the way, I have had this anomaly for a long time.  I started first with 8.04 almost a year ago (did not have it with Mepis before that) and it remained when I upgraded to 8.10 3 days ago.  

I car read and write to the floppy, so it is not a real problem.

Thanks again,

Alex

---

