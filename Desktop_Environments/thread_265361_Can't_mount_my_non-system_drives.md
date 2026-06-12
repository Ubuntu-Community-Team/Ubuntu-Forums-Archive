---
title: "Can't mount my non-system drives"
date: 2006-09-25
forum: Desktop Environments
---

### Post by bastupungen on 2006-09-25
Hello!
I could, just a couple of days ago, mount my drives just fine. Now I cannot mount them in ANY way. I think it may have been in conjunction with one of the many updates that just were done recently.

Now i can see the drives in the "computer" part of nautilus and i can see them in the "system->Disks" part of ubuntu. But i cannot do anything with them. Not through the Gui or through the CLI (mount ... -t ext3 ...)

If i try to mount them it says that the device is already mounted of busy.

What gives?

---

### Post by bastupungen on 2006-09-26
bump.

please help.

---

### Post by rogier.de.groot on 2006-09-26
Could you please post the output of the "mount" command, and tell us which drive(s) you want to mount?

---

### Post by bastupungen on 2006-09-26
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I have several sata drives that i wan't to mount, Well, ok, partitions. These are (according to system->Administration->Disks):
/dev/sdb1 /dev/sdc1 /dev/sdc2 /dev/sdc3 /dev/sdc4
/etc/fstab:
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb1	/mnt/Media	ext2	defaults	0	0
/dev/sdc1	/mnt/www	ext2	defaults	0	0
/dev/sdc2	/mnt/JonteU	ext2	defaults	0	0
/dev/sdc3	/mnt/SebbeU	ext2	defaults	0	0
/dev/sdc4	/mnt/SebbeSafe	ext2	defaults	0	0

I have been dealing with an custom kernel, to get my kernel timer at 1000hz (needed for my srcds_l server to work better) and have followed the "2.6.17 how to" here at ubuntuforums. I had to load a old kernel because I had missed iptables support while compiling the new kernel, and had to compile it all over again. There I can mount the drives and there are no problems.

I did load the old .config and checked for sata support in Qconf. So there shouldn't be any problem with the kernel. But, it obviously is.

Now if i try to do mount -a i get:
mount: /dev/sdb1 är redan monterad eller /mnt/Media är upptagen
(mount: /dev/sdb1 is already mounted or /mnt/Media is busy)

And if i try to umount any drive i get:
umount: /dev/sdb1: inte monterad
(umount: /dev/sdb1: is not mounted)
umount: /mnt/Media: inte monterad
(umount: /mnt/Media: is not mounted)

---

### Post by bastupungen on 2006-09-26
bump

---

