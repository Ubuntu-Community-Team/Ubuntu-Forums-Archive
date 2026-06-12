---
title: "Usb Disk Error"
date: 2005-12-17
forum: Desktop Environments
---

### Post by dvejnovic on 2005-12-17
I have KUbuntu 5.10. If I login as root or as user with sudo rights the USB disk was automount and I can read the file from it. But if I login as normal user, I can't read contents from USB disk.
 
 What's wrong?

---

### Post by amohanty on 2005-12-17
Can you post the contents of your /etc/fstab file?

---

### Post by dvejnovic on 2005-12-19
[QUOTE=amohanty]Can you post the contents of your /etc/fstab file?[/QUOTE]
-----------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc2       /boot           ext3    defaults        0       2
/dev/hdc3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by amohanty on 2005-12-19
Is this an external USB hard drive or is this a memory card?

---

### Post by One Quick Question on 2005-12-20
If you have Ubuntu stuff installed, run *users-admin* and make sure "Enable access to external storage devices automatically" is enabled under the "User privileges" tab of your user properties.

With *kcontrol* there is a few more clicks to do.  Under "System Administration" > "Users & Groups", pop into admin mode, modify your user, and then add yourself to the secondary group *plugdev*.

That ought to do it.

I hope.

---

### Post by aysiu on 2005-12-20
[QUOTE=One Quick Question]
With *kcontrol* there is a few more clicks to do.  Under "System Administration" > "Users & Groups", pop into admin mode, modify your user, and then add yourself to the secondary group *plugdev*.[/QUOTE] Here's a visual translation.

---

### Post by One Quick Question on 2005-12-20
Aha!  That's done with *kdesu kuser*.  Much less clicking than with using KControl!
Find your username, doubleclick, click on the Groups tag, and there you go.

---

### Post by Krash1201 on 2005-12-28
i am having similar problems with my external usb harddrive.  its a sata to usb hdd enclosure.  plugdev is checked for my user account.  the output of my /etc/fstab follows:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/windows2k ntfs    umask=0222 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3	/media/storage vfat umask=000 0 0

automount works fine for cdroms, but for some reason my external hdd won't work.  any ideas?  thanks in advance.

---

