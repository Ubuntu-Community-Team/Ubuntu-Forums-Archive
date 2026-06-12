---
title: "Yet another NTFS mounting thread."
date: 2006-07-13
forum: Desktop Environments
---

### Post by Flaystus on 2006-07-13
Ok I see the info all over the place with the 

/dev/hda1            /windows/C           ntfs       noauto,ro,users,gid=users,umask=0002,nls=utf8 0 0

What I need to know is this.
I have 3 partions. 1 on my primary drive, 2 on a secondary drive that are all NTFS.

1. How can I figure out the exact lines to add for each of them.

and much less important..

2. Why when I click on computer I see them but can't mount them (you would think at this point linux would know what to do at this point)

3. Why hasn't someone written a simple tool for this?

---

### Post by randell6564 on 2006-07-13
Post your /etc/fstab

You can see them but cant mount them because you dont have them added to your fstab.

go here [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) and find your solution.

---

