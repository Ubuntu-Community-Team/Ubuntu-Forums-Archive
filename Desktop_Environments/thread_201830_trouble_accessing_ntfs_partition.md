---
title: "trouble accessing ntfs partition"
date: 2006-06-22
forum: Desktop Environments
---

### Post by dtrizzle on 2006-06-22
I just installed Ubuntu on my laptop and it is now dual boot.  I can't seem to access my windows partition. 

After my install, the ntfs partition automatically appeared in Places -> Computer as "36.5 GB Volume."  However, when I double click it, I get the message "Unable to mount selected volume" Under show more details, it says "error: device /dev/hda1 is not removable” AND “error: could not execute pmount.”

My default fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



I then added this line to my fstab file:
/dev/hda1       /media/windows  ntfs  uls=utf8,umask=0222   0       0

Now I get almost the same error message.  Under show more details, it says "mount: only root can mount /dev/hda1 on /media/windows."

When I type “fdisk –l” the ntfs partition is actually listed first as /dev/hda1 but I don’t know how to access it given the errors above.

Does anyone know how I can access my windows partition in Dapper?  Thank you in advance for your help.

Dtrizzle

---

### Post by aysiu on 2006-06-22
Your fstab entry is almost good. ```
/dev/hda1 /media/windows ntfs **nls**=utf8,umask=0222 0 0
``` After you change the /etc/fstab, though, you need to either ```
sudo umount /dev/hda1
sudo mount -a
``` or reboot your computer in order for the changes to take effect.

---

### Post by dtrizzle on 2006-06-22
Thank you very much.  It works perfectly now!

Dtrizzle

---

