---
title: "Dual Boot WinXP Ubuntu 8.10, partition problem"
date: 2009-04-01
forum: General Help
---

### Post by terrorsathan on 2009-04-01
-

---

### Post by 3Miro on 2009-04-01
No clue!

Did you try renaming the drive from within windows. I think it is possible to assign an arbitrary drive letter. You can do that for network drives.

Does it ask for a drive letter when you first formated the partitionf orm the windows installer?

---

### Post by markharding557 on 2009-04-01
is it picking up a removable drive as c

---

### Post by GepettoBR on 2009-04-01
> **3Miro said:**
> No clue!

Did you try renaming the drive from within windows. I think it is possible to assign an arbitrary drive letter. You can do that for network drives.

Does it ask for a drive letter when you first formated the partitionf orm the windows installer?

That would be: right-click My Computer, select Manage, go to Disk Manager.

I don't know i it'll let you change the drive letter of the installation drive, though.

markharding557 might be on to something.

IIRC, the installer lets you choose the drive letter, though.

---

### Post by ajitem on 2009-04-01
Yeah, try renaming the drive from within Windows. To do this, right-click on My Computer->Manage. In the Disk Management Console, go to the properties of concerned drive and select a suitable drive letter from under Select Drive Letter drop down. 

Click OK and restart !

---

### Post by terrorsathan on 2009-04-01
-

---

### Post by terrorsathan on 2009-04-03
-

---

### Post by terrorsathan on 2009-04-03
-

---

### Post by terrorsathan on 2009-04-05
-

---

### Post by Bucky Ball on 2009-04-05
Could you post the output of:

```
sudo blkid
```

... please?

---

### Post by terrorsathan on 2009-04-05
-

---

### Post by Bucky Ball on 2009-04-05
That's all fine, everything is fine. My /proc/mounts looks exactly the same and is mounting at both / and 
/dev/.static/dev. I would say 'normal', forget it, move on and explore your system. :)

```
/dev/disk/by-uuid/36bd7710-ca84-48c9-9011-e96d336ba192 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/disk/by-uuid/36bd7710-ca84-48c9-9011-e96d336ba192 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
```... not exactly the same, but that is fine. You're up and running by the looks.

---

### Post by terrorsathan on 2009-04-05
-

---

