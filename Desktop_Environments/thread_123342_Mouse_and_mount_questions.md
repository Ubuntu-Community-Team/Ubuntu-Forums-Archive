---
title: "Mouse and mount questions"
date: 2006-01-29
forum: Desktop Environments
---

### Post by sixsparkle on 2006-01-29
I'm sure I'm just missing it, but I can't find anywhere to actually configure my mouse buttons in Gnome on Breezy.  I'm using a Logitech Mouseman cordless - the hardware detected fine.  I want to configure the wheel button with the 'back' function in my browser.  I'm also wondering if I can add a 'logout' shortcut to the desktop menu when I right-click.

Also, the default mounts for my non-linux partitions all show up on my desktop, but I can't access them.  I have to go through Disks (yay Automatix!).  It tells me I don't have permission, even though I edited all permissions in Users and Groups, it still tells me that the owner is root.

*sigh*

I'm sure I just skipped over these fixes since I'm cross-eyed from staring at my monitor for 6.5 hours.  I wish I made enough money to not have to cram all my computing time into my Sunday afternoons and evening.  Who's with me?

Any help would be greatly appreciated.

---

### Post by RAOF on 2006-01-29
I'd check out your /etc/fstab file, as per [this wiki page]("https://wiki.ubuntu.com/AutomaticallyMountPartitions").

---

### Post by sixsparkle on 2006-01-29
Thanks!  They're all working fine!

---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hdb5 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdb7 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda1 /media/hda1 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/hda5 /media/hda5 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/hda6 /media/hda6 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/hdb1 /media/hdb1 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/sda1 /media/sda1 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/sda5 /media/sda5 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/sda6 /media/sda6 ntfs defaults,uid=1000,gid=1000,auto,rw,user 0 0
/dev/hdb6 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

One down, one to go.  On to the mouse config...

---

