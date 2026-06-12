---
title: "Ubuntu on Dell N5010"
date: 2010-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaspreet2142 on 2010-10-23
I buoght new Dell N5010 when i tried to install ubuntu using wubi installer inside windows, it install fine and complete without giving any error but when i reboot and boot into ubuntu it starts setting first time configuration and gives me error "please define the root drive"

do i need driver for hard disk?

---

### Post by jaspreet2142 on 2010-10-24
is there no one who can help me ?

---

### Post by safwankhan on 2011-03-31
While installing, most probably you did not specify the root partition which would have then been treated as the Linux root partition for your Ubuntu. I suggest that you re-install ubuntu and this time, select [SIZE=3]**/**[/SIZE] as the mount point of your ext4 partition on which Ubuntu is going to be installed. You will have to manually select the partitions during Ubuntu Setup for the sake of accessing these options. In case of swap partition, there is no need of a mount point. :)

---

