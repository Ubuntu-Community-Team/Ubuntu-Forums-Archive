---
title: "problem with mounting windows NTFS drives"
date: 2008-12-12
forum: General Help
---

### Post by arunmib on 2008-12-12
Hey all, I got ubuntu 8.10 installed in my laptop with winXP home (SP3)...when I installed ubuntu, i edited the /etc/fstab so that both my windows drives are mounted in RW mode for all users...it was working fine for a month and one fine day it magically stopped working, meaning i'm not able to access my windows drives anymore. they are not getting mounted in the usual way once the system boots...but I'm able to mount them manually and use them...any clue what is the problem or what information do you ppl. need to help me fix this thing?

---

### Post by biotrox on 2008-12-12
can u check if the ntfs module is loaded?
#lsmod | grep -i ntfs

if it's not try putting it in the /etc/modules

hope this helps

---

### Post by kuhlbeans on 2008-12-13
Anything in the system logs concerning the failed mount?

---

### Post by arunmib on 2008-12-13
nope guys...both didn't help... :(

---

### Post by arunmib on 2008-12-13
sorry guys...it was my mistake...i was such an dumb idiot....i was trying to access the windows drives through the links for mount points that I created in the desktop....but actually the mount point dirs were missing :( ...how did this happen I've got no clue...but still wondering why I didn't get any error messages???

---

