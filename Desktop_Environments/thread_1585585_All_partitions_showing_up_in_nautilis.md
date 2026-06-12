---
title: "All partitions showing up in nautilis"
date: 2010-09-30
forum: Desktop Environments
---

### Post by fugaki on 2010-09-30
I set up a new copy of 10.04, and I encrypted each partition. Now, all of the partitions show up in nautilis.

I have two drives, one has /home, and the other has /, /boot, and a swap area.

Correction, /bbot does not show up, but all of the others show up in nautilis(including swap), but I can't open them, I can just access them normally through /

Does anyone know how I can hide these?

Thanks.

---

### Post by blueturtl on 2010-10-01
The Ubuntu Places menu usually shows file systems that are not automatically mounted on startup (ie. listed in /etc/fstab).

If the file systems are not indicated in the file, Ubuntu will treat them as if they are pluggable media like USB thumbdrives.

Do you have them in /etc/fstab?

---

