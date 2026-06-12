---
title: "how do i get partitions in nautilus but not on desktop ?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by jamesford on 2005-10-20
hi

ive been adding 'user' to the lines in fstab, and i really love having all my partitions shown in the tree view in the left pane of nautilus. but they also appear on the dekstop, which i dont want. is there a way to get these partitions in theleft tree window in nautilus but NOT on my desktop ? i know u can set it up so that mounted drives do not show on desktop but tht means inserted cds or dvds dont show either and i want those to show...just not the harddisks..man i guess im bad at explaining. do anyone understand what i mean?

---

### Post by Stormy Eyes on 2005-10-20
Post your /etc/fstab, please. I want to be able to give you the exact commands you'll need along with an explanation of how they work.

---

### Post by afonic on 2005-10-20
If you open the configuration editor,  apps -> nautilus -> desktop and uncheck "volumes_visible" then all the mounted drives will not show in the desktop. (but they will show in Places menu).

This affects CDROMs as well (they don't show up), but I don't know a way to have just the CDROMs show in the desktop when mounted and the mounted hard disks no.

---

### Post by jamesford on 2005-10-20
stormy eyes, my fstab:
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /home/username/Drives/Documents  ext3    defaults,errors=remount-ro 0     1
/dev/hdb1       /home/username/Drives/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb2      /home/username/Drives/linbackup      ext3    defaults,errors=remount-ro 0       1
/dev/hda1      /home/username/Drives/misc    ext3    defaults,errors=remount-ro 0       1
---
afonic:
thats what i fouind out too..i want the cd/dvds on desktop just not the harddisk partitions :/

---

### Post by Stormy Eyes on 2005-10-20
**jamesford**, I need to take a look at what **afonic** mentioned before I tell you to do anything. Can you wait until tonight, when I've tested everything on my Linux box at home, before I give you a HOWTO?

---

### Post by jamesford on 2005-10-20
stormy, its already tonight here ;)

but ill wait, ive bookmarked the page so whenever you got the solution ill find it as long as u post it here :)

thanks

---

### Post by Stormy Eyes on 2005-10-20
**jamesford**, I have to apologise, as I misunderstood your question. After reading the manual and poking around in gconf, I don't see any means of disabling display of mounted hard drive volumes on the desktop but not mounted CD-ROMs. I'm sorry to have disappointed you.

---

### Post by jamesford on 2005-10-21
ah too bad, well thanks anyway :)

---

