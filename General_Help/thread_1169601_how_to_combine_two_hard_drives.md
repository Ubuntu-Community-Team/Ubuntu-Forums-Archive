---
title: "how to combine two hard drives"
date: 2009-05-25
forum: General Help
---

### Post by threemoons on 2009-05-25
hi  I have a server with 2 hard drives but when I installed ubuntu it just installed on the one drive. Is there a program that can merge both drives so that there memory capacity is seamless available to me instead of need to search for the second drive and mount it or whatever must be done? The installation was done as an encrypted LVM.

---

### Post by HotForLinux on 2009-05-25
It's easy  to make Linux mount the other disk at boot time. You just need to add a line in the fstab configuration file:

/etc/fstab

Then both file systems will be merged seamlessly, as long as linux can work with the other one

---

### Post by threemoons on 2009-05-25
> **HotForLinux said:**
> It's easy  to make Linux mount the other disk at boot time. You just need to add a line in the fstab configuration file:

/etc/fstab

Then both file systems will be merged seamlessly, as long as linux can work with the other one

thanks for replying - my fstab entry showing the first drive is commented out - I never saw that before - how should I add my entry for the second drive in this case?

---

### Post by HotForLinux on 2009-05-25
The first is commented and you want to add the second?

I don't know. That depends on the number and type of  partition(s?) you have there and on the place (directory) you want to see them mounted  (do you clearly understand this concept?). 

Why don't you post the output of 

**$ cat /etc/fstab**

and explain also what partitions have you got. That is, paste the output of  executing

**$ sudo fdisk -l**

in the bash shell

---

