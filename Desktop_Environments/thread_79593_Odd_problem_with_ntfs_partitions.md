---
title: "Odd problem with ntfs partitions"
date: 2005-10-20
forum: Desktop Environments
---

### Post by medvej on 2005-10-20
Hello all!
The problem is:
partitions are mounted, fstab as follows:
/dev/sda1       /windows        ntfs    nls=utf8,umask=0222       	0       0
/dev/sda5       /winstorage1    ntfs    nls=utf8,umask=0222        	0       0
/dev/sda6       /winstorage2    ntfs    nls=utf8,umask=0222        	0       0
/dev/sda7       /winstorage3    ntfs    nls=utf8,umask=0222        	0       0

But can not see the contents -"permission denied" both in terminal and GNOME.
've tried:
sudo chmod 444 /winstorage3
and:
sudo chmod 666 /winstorage3

it looks successfull, but the result is the same.
Any ideas, please?
Thank you in advance.

---

