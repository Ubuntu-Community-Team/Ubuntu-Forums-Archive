---
title: "list of installed packages on crashed ubuntu"
date: 2009-05-18
forum: General Help
---

### Post by trl on 2009-05-18
server has crashed hard drive

I have the drive connected by usb on
another machine, and I am wondering how
to get the package list so that I can install
on a new drive.

I can only find instructions that require a
working installation.

---

### Post by Titan8990 on 2009-05-18
First you need to chroot in to the install: 

```
mount -t proc none /media/MOUNT/proc
mount -o bind /dev /media/MOUNT/dev
chroot /media/MOUNT /bin/bash
source /etc/profile
```

Make sure you replace /media/MOUNT with the path to your mount point.


The following commands gives installed packages on a system:


sudo dpkg &#8211;get-selections


Otherwise you may need to parse through /var/lib/dpkg/status


In the future, you should make backups.

---

### Post by trl on 2009-05-18
That worked!  

thanks

---

### Post by trl on 2009-05-18
Actually I did this:

dpkg --get-selections

---

### Post by Titan8990 on 2009-05-19
Good to hear.

---

