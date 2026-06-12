---
title: "How to use an NTFS external USB hard drive"
date: 2006-09-01
forum: Desktop Environments
---

### Post by cleentrax on 2006-09-01
I have an old 60gb drive that I stuck in an external case to use for backup. It was NTFS formatted, and I couldn't write to it with Ubuntu, so I used fdisk and mkfs to delete/create a new partition, and format it with ext3.

Now I can't write to it -- it says I don't have permission.

How do I get permission? chmod doesn't change anything. Nor does using Nautilus with root access. In general, I'm confused and annoyed by permissions in Linux, and this is another example.

help please!

EDIT: I should add that what I'm trying to backup is the NTFS partition on my laptop hard drive (windows XP) so that I can reformat and do an Ubuntu-only install.

---

### Post by huangjiahua on 2006-10-10
I think you can use ntfs-3g,
[http://ubuntuforums.org/showthread.php?p=1601663](http://ubuntuforums.org/showthread.php?p=1601663)

---

