---
title: "help desprate pls :) prob with access fat32"
date: 2005-11-29
forum: Desktop Environments
---

### Post by trandojedi on 2005-11-29
hi... i want to access a partion on my harddrive that i made in ubuntu 5.10.  When i installed my system, i installed windwos first - so in the windows installer i made a partition for windows (NTFS), a small 2gb fat32 partiton that i wish to like use to write to in linux and windows, and the rest i left as 'free space' which i later installedd ubuntu on.  I mangaged to auto mount my windows partition by editing the /etc/fstab file, adding the line
/dev/hda1  /media/windows  /ntfs  nls=utf8,umask=0222  0  0
i got this from some guide and it worked...

how would i go about auto mounting my fat32 partition so that i can read an write to in in ubuntu... cheers garrick

---

### Post by aysiu on 2005-11-29
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

