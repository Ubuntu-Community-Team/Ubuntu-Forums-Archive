---
title: "Cannot find my other HD partitions"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Ray Fried on 2005-05-16
Can someone tell me how to access the FAT and NTFS partitions on my hard drive? When I type fdisk from my terminal window, I get a response "cannot open /dev/hda".  I have only one IDE drive on this machine with 4 different partitions.

I have tried fdisk -l and various things but obviously not the correct text.

Thanks,

Ray

---

### Post by dave9191 on 2005-05-16
Hey Ray, 

when you try to fdisk, you must issue that as a super user. 'sudo fdisk' and enter you password. As an unprivlaged user you are not allowed to access that. As for mounting FAT and NTFS filesystems take a look [here](http://ubuntuguide.org/#mountunmountntfs) .

Dave

---

### Post by Ray Fried on 2005-05-18
Thanks Dave. I had overlooked the "sudo"!!! Things working now!!

Ray

---

### Post by dave9191 on 2005-05-18
No probs man. Glad I could help :)

---

