---
title: "Confused my disk usage analyser"
date: 2009-06-20
forum: General Help
---

### Post by John M2009 on 2009-06-20
I want to find out how much free space I have on my hard disk,  I know the partition that Ubuntu is installed on is 104GB (I know it sounds rather large,  but I decided to keep all my files in one place rather than creating seperate partitions for everything...wanted to keep the installation simple)  I scanned the file system using the disc usage analyser, and it shows I have only 54GB used on "/"  but the usage shows 100%  There is also a whole other list of places like home,  media, usr which show a percentage of usage as well as how much is used,  I thought home media and usr etc... were directories,  or whatever the Linux equivalent of a windows directory is?  Or does Linux allocate a certain amount of disk space for each directory?

---

### Post by drs305 on 2009-06-20
The top level of DUA always shows 100%. If you go to the link in my signature line to the Recover Lost Disk Space wiki it will give you techniques for using DUA as well as other methods to determine what you really have on your disks.

Here's a sample:
```

df -Th | grep "/dev/sd"
sudo du -h / --max-depth=1 | sort

```

---

