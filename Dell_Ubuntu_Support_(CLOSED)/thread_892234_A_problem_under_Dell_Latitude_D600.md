---
title: "A problem under Dell Latitude D600"
date: 2008-08-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alun1994 on 2008-08-16
After I installed Ubuntu 8.04 Server under Dell Latitude D600,
then it restart the laptop and show me this code:

```
The kernel requires the following features not present on the CPU
0:6
Unable to boot - please use a kernel appropriate for your CPU
```
Anyone can help me to fix it?
Thank you for your reading...:)

My laptop config:
Intel Pentium M 1.7GHz
1GB RAM
55GB HDD

---

### Post by eggie9001 on 2008-08-17
Try downloading the Desktop edition, not the server edition.

:)

---

### Post by dstorrez on 2008-08-17
Server edition cannot run on a mobile processor.

---

### Post by MadEgg on 2008-09-12
> **alun1994 said:**
> After I installed Ubuntu 8.04 Server under Dell Latitude D600,
then it restart the laptop and show me this code:

```
The kernel requires the following features not present on the CPU
0:6
Unable to boot - please use a kernel appropriate for your CPU
```
Anyone can help me to fix it?
Thank you for your reading...:)

My laptop config:
Intel Pentium M 1.7GHz
1GB RAM
55GB HDD

You can do this, you just need another kernel. After installation, boot from the CD and select rescue a broken system.

Switch to another console(Alt+F3 or something), hit enter, mount the root partition on /mnt and bind /dev: 
```

mount /dev/sda1 /mnt
mount -o bind /dev /mnt/dev

```
enter a chroot:
```

chroot /mnt /bin/bash

```
and install another kernel, removing the old:
```

apt-get install linux-generic
apt-get purge linux-server linux-image-server

```
Finally, you need to update grub:
```

update-grub

```

Then reboot and it should work:
```

exit
umount /mnt/dev
umount /mnt
reboot

```

---

### Post by crazysteve on 2008-09-12
I am having the same issue. After installation, I boot from the CD to "Repair Broken System". Once I select this the installation process starts over again, prompting the user for a language. 

Any ideas? Is this the only way get the command line prompt?

---

