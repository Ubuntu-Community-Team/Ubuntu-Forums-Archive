---
title: "Manual mount always yields read-only"
date: 2009-02-05
forum: General Help
---

### Post by Kralizec on 2009-02-05
I've searched the forums fairly thoroughly and haven't seen this particular problem. That being said, I may just be doing something incorrectly and I haven't caught it yet.
  I have a FAT32 partition that I share between my Windows and Ubuntu partitions. I want this to automount in Ubuntu at startup because my wallpaper and torrent folders are on this partition. I have created a folder for it to mount to (the one Nautilus mounts it to when I access it via the Places menu, i.e. /media/disk/). When I add the fstab entry for the device: ```
/dev/sda6 /media/disk/ vfat <my options> 0 0
```and then try to run *mount -a*, it mounts the partition successfully but I cannot write to it (create, cut, delete files). The options I have used include *users*, *rw*, and various *umask* codes. None of these have worked. 
  When I mount the partition on the command line using the *mount* command, I have the same problem. I have ensured I am the owner of the mount point and have read/write permission to it. I am able to write to the partition after mounting via the Places menu. I've read many fstab tutorials so I would prefer not to be linked to another one. I would not be asking for help here if I could figure it out from a tutorial.
  I hope someone can shed some insight on my problem because I've been struggling with this issue for some time now.

---

### Post by drs305 on 2009-02-05
With non-linux file systems (at least with ntfs and vfat), the owner is set at the time of mounting, and whoever mounts it owns the mount point. Often this is 'root', but you should still be able to read/write to it by clicking on the device.

You can make yourself the owner by including the following in your fstab setting: "uid=1000" (assuming you are the user with id 1000). You can check by running "id" in the command line. So an fstab entry which gives uid 1000 ownership might look like this:
```

UUID=1838-39498-0356-f6d9 /media/mydata ntfs auto,users,uid=1000,umask=027,utf8 0 0

```

"mount -a" should now allow you to read/write.

---

### Post by Kralizec on 2009-02-06
Thanks, that's exactly what I needed. And it makes sense why it was necessary.

---

