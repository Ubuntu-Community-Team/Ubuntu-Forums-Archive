---
title: "Rename a partition!"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Tubbie on 2005-11-08
I want to change the name of my partition on my harddisk from 'ftp' to 'data1',
but I have no idea how to do it.
I don't get permission to rename the partition.
Anyone know how to do this and that it mounts the drive again automatically?

Probably it isn't that hard, but I'm not that common with mounting things and stuff like that.:oops: 

Thanks already!

---

### Post by Pablo_Escobar on 2005-11-08
You don't rename partitions in Linux :) It's a Window$ thing.
You just select an other mount point.
It's all in /etc/fstab file.

---

### Post by Tubbie on 2005-11-08
Thanks, that worked.

I changed the name in the file fstab from '**ftp**' to '**data1**'.
Then I changed the foldername '**ftp**' to '**data1**'
and went to **System > Administration > Disks**
Finally I pushed the button **Enable** bij the right partition :)

---

