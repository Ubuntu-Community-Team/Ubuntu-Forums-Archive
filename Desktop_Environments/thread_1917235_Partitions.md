---
title: "Partitions"
date: 2012-01-29
forum: Desktop Environments
---

### Post by mibtech on 2012-01-29
This might be a dumb question but,

I am running ubuntu 11.10

I created a large partition as a second drive but I have to dig under file system to access it and it won't let me make a link to it I want it to show up as a device like its a hard disk of its own. is this possible?

---

### Post by heshoots67 on 2012-01-29
[URL="https://help.ubuntu.com/community/Installation/SystemRequirements"]https://help.ubuntu.com/community/Installation/System
Requirements[/URL]

Try this if it works.

---

### Post by ajgreeny on 2012-01-29
I don't quite understand exactly what you mean, but it sounds as if you have a partition separate from your ubuntu install that you wish to use as a data drive.

How is it formatted, ie what filesystem, fat32, ntfs, ext#?
Where is it mounted; it is probably in /media, but if not where, or do you have to mount it manually with a command?

Please run the commands ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
``` one by one and copy the output of each back here.

---

