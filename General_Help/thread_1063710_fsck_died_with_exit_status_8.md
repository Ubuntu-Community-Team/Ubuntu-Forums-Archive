---
title: "fsck died with exit status 8"
date: 2009-02-08
forum: General Help
---

### Post by Jeztastic on 2009-02-08
Hi,

I recently upgraded my sister and brother in law's PC to 8.10. All well and good, but I was just about to take it back to her, and turned it on to check a couple of things. I got the above error message.

I have hunted around, and I clearly need to change the UUID in fstab. 

```
sudo vol_id -u sdb1
```

However, the system will not recognise the drive to give me the correct UUID.

```
/dev/sdb1: error opening volume
```

Please help! My brother in law has developed a facebook addiction and is hassling me to get it back!

Edit: The root partition is fine, it is /home on a seperate hard drive that is the problem. I updated root but did not touch the home partition.

---

### Post by plucky on 2009-02-09
From a terminal post output of ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
``` -l is lowercase L not a 1

---

### Post by Jeztastic on 2009-02-14
I just tried to find the drive using a live CD, and the second HDD was not even recognised. Does this mean it's died? How do I know for sure? I'm afraid I can't easily post the output of commands because I have no way of copy and pasting them here.

---

