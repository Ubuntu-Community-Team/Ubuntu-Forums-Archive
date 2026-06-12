---
title: "What should partition be mounted as?"
date: 2008-12-15
forum: General Help
---

### Post by Het Irv on 2008-12-15
I am setting up a Fedora - Ubuntu dual boot, and one of the new partitions is a "shared data partition".  My question is.. what should this be mounted as?

---

### Post by taurus on 2008-12-15
You could mount it to /media/share!

---

### Post by Het Irv on 2008-12-15
is that what I should set the mount point to when creating the partition?

---

### Post by taurus on 2008-12-15
You first need to create a partition.  Then format it.  After all that, then you need to mount it somewhere so use /media/share if you wish.

---

### Post by Het Irv on 2008-12-15
I get that much, but when I create the partition in the installer, it gives me an error saying that because there is no mount point assigned for sda7, that it will not be used....

wait that means that the partition will still be availible... just not used in the install doesn't it?

---

### Post by taurus on 2008-12-15
Then tell the installer to mount /dev/sda7 to /media/share.  Otherwise, you can add an entry in /etc/fstab for /dev/sda7 later if you wish.

---

### Post by Het Irv on 2008-12-15
okay, that makes sense, i just wasn't sure, didn't want to kill it somehow.

---

