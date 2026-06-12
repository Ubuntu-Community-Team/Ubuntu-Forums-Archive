---
title: "NTFS widows partition mount point?"
date: 2009-04-28
forum: General Help
---

### Post by fbp90crx on 2009-04-28
I am trying to load Jaunty on my machine that already has XP on it. I resized the NTFS partition to where I want it and built the Linux and swap partitions. I mounted the linux partition at /. It is telling me "there is no mount point assigned for ntfs file system in partition#1. If you do not go back to the partitioning menu and assign a mount point from there, this partition will not be used at all."
Do I need to mount the NTFS partition?

---

### Post by dcstar on 2009-04-29
> **fbp90crx said:**
> I am trying to load Jaunty on my machine that already has XP on it. I resized the NTFS partition to where I want it and built the Linux and swap partitions. I mounted the linux partition at /. It is telling me "there is no mount point assigned for ntfs file system in partition#1. If you do not go back to the partitioning menu and assign a mount point from there, this partition will not be used at all."
Do I need to mount the NTFS partition?

If you want access to the files automagically, yes. Just do this:

```
sudo mkdir /Windows
```
and you will have a mountpoint called "Windows", then install the **pysdm** package and use it to set up the mount.

---

