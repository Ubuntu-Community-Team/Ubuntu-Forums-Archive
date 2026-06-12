---
title: "error:  error: device /dev/hdb1 is not removable"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-18
Hello

I have a new hard drive and when I go to Places<Computer it is gives me the following error
error: device /dev/hdb1 is not removable

> error: device /dev/hdb1 is not removable

error: could not execute pmount

I have Formatted the drive and enabled it and I still get this error !  What the heck is the problem??  I cant figure it out

---

### Post by bswilson on 2006-09-18
> **Magiczero said:**
> error: device /dev/hdb1 is not removable

There's probably nothing wrong with your drive; it's how Ubuntu is trying to mount it.  **pmount** is used to mount arbitrary hotpluggable devices as normal user.  The purpose of **pmount** is to serve as a wrapper so you can mount removable devices without a matching **/etc/fstab** entry.  

Is this what you're trying to do?  Is your hard drive a removable one or an internal drive?  I recommend that you post your **/etc/fstab** file here, as well as the output of **mount**, so we can review it and help you.

---

### Post by Magiczero on 2006-09-18
The drive is internel

---

### Post by Magiczero on 2006-09-18
Here is the file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



---

### Post by techweenie on 2006-10-29
I am having the same problem, only for /dev/sda1.  It is an internal sata drive, but linux, and even Windows, thinks it's a removeable drive.  How do I mount this to access my files?

---

