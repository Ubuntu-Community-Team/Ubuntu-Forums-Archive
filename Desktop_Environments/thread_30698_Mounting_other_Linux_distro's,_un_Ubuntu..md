---
title: "Mounting other Linux distro's, un Ubuntu."
date: 2005-04-29
forum: Desktop Environments
---

### Post by derrick1985 on 2005-04-29
Ok, I have both Ubunto and Kubuntu installed (different partitions) and right now, I need both for a little project i'm working on (you will all see soon enough) and anyways, I want to access my Kubuntu files, in Ubuntu. Right now, I can use the command sudo mount /dev/hda6 /mnt/kubuntu but it only gives me read access.

I tried to copy and paste the line from my fstab that i use for my vfat, but that doesn't work (of course, changing format to ext3 not vfat)

What command do I need to add to the fstab file?

---

### Post by nad on 2005-04-29
The command: sudo mount /dev/hda6 /mnt/kubuntu  auto-detects the filesystem type and mounts as the superuser with default options. A regular user would have read only access.

Use the line: /dev/hda6 /mnt/kubuntu ext3 rw,user,noauto  to show the mount in Places -> Computer. Then just double click to mount. You will still have read only access to files that are not yours, and as your kubuntu partition is a separate operating system, only if your uid and user name are identical to your ubuntu installation will you have write access to your files.

---

### Post by derrick1985 on 2005-04-30
[QUOTE=nad]The command: sudo mount /dev/hda6 /mnt/kubuntu  auto-detects the filesystem type and mounts as the superuser with default options. A regular user would have read only access.

Use the line: /dev/hda6 /mnt/kubuntu ext3 rw,user,noauto  to show the mount in Places -> Computer. Then just double click to mount. You will still have read only access to files that are not yours, and as your kubuntu partition is a separate operating system, only if your uid and user name are identical to your ubuntu installation will you have write access to your files.[/QUOTE]

ok, that worked perfectly, thanks.

---

