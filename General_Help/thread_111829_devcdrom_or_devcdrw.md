---
title: "/dev/cdrom or /dev/cdrw ?"
date: 2006-01-03
forum: General Help
---

### Post by pbb on 2006-01-03
NeroLinux tells me to enable DMA for my CD burner. I found some commands to do this on the UbuntuGuide, but I see that I have both a /dev/cdrom and a /dev/cdrw, even though I only have one CD/DVD drive.
For which one of these devices do I have to enable DMA? Or are they really the same?

---

### Post by Sutekh on 2006-01-07
They are the same thing...

You can check using the same code I did...
```
user@ubuntu:~$ cd /dev
user@ubuntu:/dev$ ls -l cdr*
lrwxrwxrwx  1 root root 3 2006-01-08 20:08 **cdrom -> hdc**
lrwxrwxrwx  1 root root 3 2006-01-08 20:08 **cdrw -> hdc**
user@ubuntu:/dev$

```

So cdrom and cdrw are just links to the actual device, which is hdc my CD drive.

---

### Post by bored2k on 2006-01-07
You just ```
cat /etc/fstab
``` and check which one is used there.

---

### Post by pbb on 2006-01-08
Thanks, that cleared things up for me!

---

