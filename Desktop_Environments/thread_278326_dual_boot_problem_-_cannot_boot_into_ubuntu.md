---
title: "dual boot problem - cannot boot into ubuntu"
date: 2006-10-16
forum: Desktop Environments
---

### Post by ross240 on 2006-10-16
i am using dual boot (XP+ Ubuntu 5). i used XP as the default OS from grub & set the default time as 0 sec. now i cannot go back to the GRUB screen to select ubuntu. the XP is booting fine. how do i boot into ubuntu now?:(

---

### Post by _asc_ on 2006-10-16
Hello!

Boot with the Live-CD. Then mount your Ubuntu root partition. Go to 
the /boot/grub directory of your root partition and open the file menu.lst. Then set the timeout value to a higher value (e.g. 10).

e.g. If your root partition is hda1:
```

sudo su
mkdir /mnt/ubuntu
mount -t ext3 /dev/hda1 /mnt/ubuntu
cd /mnt/ubuntu/boot/grub
gedit menu.lst

```

---

