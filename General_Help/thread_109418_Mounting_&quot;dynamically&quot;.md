---
title: "Mounting &quot;dynamically&quot;"
date: 2005-12-28
forum: General Help
---

### Post by bogoliubov on 2005-12-28
Hello. I have an iBook laptop running OSX. I mount the drive of this laptop on my PC running Ubuntu using an fstab like this:
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdd1       /mnt/extra      ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,exec,noauto  0       0
//192.168.0.2/christian /mnt/samba/ibook        smbfs   credentials=/root/.smbcredentials       0       0

The problem is that if I start the iBook after starting the PC I have to do "mount -a" in a terminal in order to mount the iBook HD. 

Is there a way to make this automatic? I guess there should be since the CD and USB devices are mounted automatically!?

---

### Post by Refrozen on 2005-12-28
If the file is in your [fstab](http://manlib.com/man/379), it will be mounted on boot, if available. To do automounting though, you need to work with one of your services. Try grepping through your services for things like mount/plug/??, and man those services.

---

### Post by bogoliubov on 2005-12-29
Thanks. I'll have a go at that.

---

### Post by bogoliubov on 2006-01-20
Hmm, I have found nothing and I don't know where to look. Is there anyone out there who has an idea for this? I'd really appreciate it!

---

### Post by Quirky on 2006-01-20
Perhaps you could use automount? This page seems like it might help

[http://uranus.it.swin.edu.au/~jn/linux/automount.htm](http://uranus.it.swin.edu.au/~jn/linux/automount.htm)

---

