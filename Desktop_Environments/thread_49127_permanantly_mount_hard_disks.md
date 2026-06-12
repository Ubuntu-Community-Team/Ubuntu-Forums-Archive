---
title: "permanantly mount hard disks"
date: 2005-07-15
forum: Desktop Environments
---

### Post by kinesis on 2005-07-15
I don't know how I can permanantly mount the hard disks of my pc. Does anyone know howhttp://ubuntuforums.org/newthread.php?do=newthread&f=65#

---

### Post by ameerirshad on 2005-07-15
I'm facing the same problem and would be curious indeed. Now I just refuse to turn of my pc or reboot ;-)

---

### Post by codejunkie on 2005-07-15
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) this might be what your looking for you have to add an entry to your /etc/fstab file for that drive so it will automount on boot hope this helps.

---

### Post by SGC on 2005-07-15
You need to add mounting entries to  /etc/fstab to mount the partitions on the statup

---

### Post by ameerirshad on 2005-08-04
Thnx I managed it :)

---

