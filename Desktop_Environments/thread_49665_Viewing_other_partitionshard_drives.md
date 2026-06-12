---
title: "Viewing other partitions/hard drives"
date: 2005-07-17
forum: Desktop Environments
---

### Post by Irony on 2005-07-17
Am I correct in saying that linux can recognise and view FAT32 partitions. I've created several partitions on my drive one of which is FAT32 but can't see it. Where would I look for the partitions.

I want to use this partition to transfer files between Windows and ubuntu and vice versa.

---

### Post by dave9191 on 2005-07-17
Have you checked the ubuntuguide.org?

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Dave

---

### Post by Irony on 2005-07-17
Thanks, that's what I was looking for - I did look earlier but missed it.

When it says;

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

Should Enter be hit after each line, or should the whole lot be pasted then a single Enter entered.

---

### Post by dave9191 on 2005-07-17
One enter after each command :) 

Dave

---

### Post by Irony on 2005-07-17
Thanks

---

