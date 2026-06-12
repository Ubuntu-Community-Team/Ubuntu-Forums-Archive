---
title: "serious problem with hdd"
date: 2006-07-21
forum: Desktop Environments
---

### Post by matko on 2006-07-21
hello all.

i get still the same error with my hdd.
i have root drive /dev/hdb1
i have /home on **/dev/hda3**

once a day i get error that system cant find /home directory, so i have to run fsck manually.
no problem but fsck always remove journal. that it convert ext3 to ext2.
so i have to convert it back to ext3.

do you know hoe to fix it?
is it big problem that i have my /home folder on other disk?

p.s. i dont have any special paramaters in hdparm.conf or fstab.

---

### Post by bDerrly on 2006-07-21
No, there is nothing wrong with having your /home on a separate partition. Can you paste an error message? Could your drive be failing physically? After someone gets a chance to look at the exact error it should be easier to diagnose the problem. Perhaps a paste of your /etc/fstab file as well.

---

