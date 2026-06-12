---
title: "free disk space"
date: 2005-03-12
forum: Desktop Environments
---

### Post by tanari on 2005-03-12
I have free 3GB on /dev/hda3 (/mnt/fat). But nautilus says: 110 MB free and I can't copy files to fat32 partition. Strange bug.

What can I do?

---

### Post by nemin on 2005-03-13
[QUOTE=tanari]I have free 3GB on /dev/hda3 (/mnt/fat). But nautilus says: 110 MB free and I can't copy files to fat32 partition. Strange bug.

What can I do?[/QUOTE]
What does df -h say?

---

### Post by tanari on 2005-03-14
> andrei@ubuntu:~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             8.9G  8.8G  103M  99% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev/hda3             9.9G  9.8G  110M  99% /mnt/fat
/dev/hdb1              75G   37G   38G  50% /mnt/ntfs


But when I reboot to winXP I can see there 3GB free space!

---

### Post by nemin on 2005-03-14
[QUOTE=tanari]But when I reboot to winXP I can see there 3GB free space![/QUOTE]
Hmm that's really strange. I better believe Ubuntu than Windows ;) Try to put a few hunderds of MBs on the partition with Windows, I bet that won't work :)

---

### Post by tanari on 2005-03-15
I have installed bloodlines on winxp (~2.5 GB) and have 400 MB free space.
Something strange with ubuntu :). But soon I will format it and install hoary :) (when final version will be available).

---

