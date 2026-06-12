---
title: "How to see what process is locking file, directory, device, etc"
date: 2009-06-22
forum: General Help
---

### Post by pythonscript on 2009-06-22
Is there a way on ubuntu to see what process is locking a file, directory, or a device? I'm trying to unmount /dev/sdb1 (in this case, a western digital removable hard drive) and it refuses to unmount. This device is impossible to remove under windows (as in, safely remove hardware refuses to work, no matter what I try) and I'm hoping the same problem isn't materializing under ubuntu. How can I see what, if anything, is locking the device? Thanks in advance!

---

### Post by geirha on 2009-06-22
The following should list all processes that uses /dev/sdb1
```
sudo fuser -cv /dev/sdb1
```

---

### Post by pythonscript on 2009-09-06
Thanks, that's what I was looking for!

---

