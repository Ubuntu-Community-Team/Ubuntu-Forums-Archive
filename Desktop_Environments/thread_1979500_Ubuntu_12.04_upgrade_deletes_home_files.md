---
title: "Ubuntu 12.04 upgrade deletes home files"
date: 2012-05-13
forum: Desktop Environments
---

### Post by shadysamir on 2012-05-13
I had Ubuntu 11.04 32bit installed with 5 users. Home folder has its own partition. I was planning to install Ubuntu 12.04 64bit so I booted from the live CD and was going to manually select partitions. This was going to remove all installed packages but would have kept all user files and settings. I saw a new option for installation that said Upgrade to 12.04 while keeping all files and most packages. I thought greate. But after installation none of the packages were there, also all user folders under home were empty. The folders were there, but all files were gone. Only default empty folders for each user were there.

I dont care much for packages, all I want is to get the files that were under each user home folder back!

---

### Post by rg_stephens on 2012-05-13
The old home partition and files are probably still there, but when you installed you didn't select that partition to be used as /home. If you open Disk Utility you can find and mount that partition to find your files...

---

### Post by shadysamir on 2012-05-13
I actually just found out that. Original home partition was not touched. Since I chose that Ubuntu should do the upgrade for me I expected it to detect home partition and keep it. This didnt happen. The root partition was used in full. The weird thing is, all user folders under new home were created!

---

