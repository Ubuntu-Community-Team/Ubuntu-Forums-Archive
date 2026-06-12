---
title: "How do I format an external hard drive?"
date: 2009-05-29
forum: General Help
---

### Post by arashiko28 on 2009-05-29
I want to format my 100GB hard drive from my old computer and adapt it as an external hard drive, that is already done, now, on the the drive I have Ubuntu 7.10 and windows xp, I want to format it and make one full partition again, how do I do it?
I think it's good to mention that I already tried this once and fried my flash drive, :(

---

### Post by arashiko28 on 2009-05-29
BUMP!!!

Hello?? I need help... I don't get very well the instructions I have found. I thinks it's good to make clear that the USB hard drive is IDE and the actual laptop drive is SATA.

---

### Post by arashiko28 on 2009-05-29
I now know that the partitions are /dev/sdb1 and /dev/sdb3, now... I want to delete them both and make one single partition. Please help!

---

### Post by bacardiandwatermelon on 2009-05-29
Hey, sorry I'm a bit confused. So you have a laptop hdd with a dual boot xp and ubuntu on it, you want to remove one and put it on the external drive? And then resize the laptop hdd partition so it fits the rest of the laptop drive?

---

### Post by SpaceBison on 2009-05-29
I'm not sure what you want to do exactly, but if you have it handy, your Ubuntu disk has a partition editor on it which you can use to resize/delete/format/etc your drive.

---

### Post by arashiko28 on 2009-05-29
No.

I have a laptop hd, with two partitions, one with xp and the other one with ubuntu. I already took it out and placed it on a external case and plugged it to a usb port.

All of the instructions I have found are about formating one partition disks. I want to format the disk and make it one single partition again to use it as a external drive.

---

### Post by SpaceBison on 2009-05-29
Ok yeah, you can do that using gparted, which is already on the Ubuntu cd. Or you can install it using the package manager.

---

