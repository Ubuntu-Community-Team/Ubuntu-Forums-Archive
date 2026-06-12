---
title: "Issue with BackInTime"
date: 2012-07-26
forum: Desktop Environments
---

### Post by jpaulb on 2012-07-26
I am having an issue with Backintime version 1.0.8-1. I have Ubuntu 12.04 installed but am using Xubuntu.
Every time I try to backup my home directory it fails with the warning Failed to take snapshot 12-07-26 12:18:02 !!!

The log shows the following:
```
[I] Take snapshot
[I] rsync -rtDH --links --no-p --no-g --no-o  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="/media/Backup" --exclude="/home/jpb/.local/share/backintime" --include="/home/jpb/" --include="/home/" --exclude=".gvfs" --exclude=".cache*" --exclude="[Cc]ache*" --exclude=".thumbnails*" --exclude="[Tt]rash*" --exclude="*.backup*" --exclude="*~" --exclude="/home/jpb/Ubuntu One" --exclude=".dropbox*" --include="/home/jpb/**" --exclude="*" / "/media/Backup/backintime/Maple/jpb/1/new_snapshot/backup/"

[I] Take snapshot (rsync: rsync: opendir "/home/jpb/.config/nautilus-actions" failed: Permission denied (13))
[E] Error: rsync: opendir "/home/jpb/.config/nautilus-actions" failed: Permission denied (13)

 Take snapshot (rsync: rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9])
```

---

### Post by brainwash on 2012-07-27
Either exclude the folder "/home/jpb/.config/nautilus-actions" from the backup process or change permissions for this folder.

---

### Post by jpaulb on 2012-07-27
> **brainwash said:**
> Either exclude the folder "/home/jpb/.config/nautilus-actions" from the backup process or change permissions for this folder.

Thanks.

Changing the permission works, nautilus-actions was automatically installed when installing Backintime. Should the installer not set up the proper permissions?

---

### Post by brainwash on 2012-07-27
It's a confirmed bug. The permissions on that folder are messed up.

[https://answers.launchpad.net/ubuntu/+source/nautilus-actions/+question/194838](https://answers.launchpad.net/ubuntu/+source/nautilus-actions/+question/194838)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/1000543](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/1000543)

---

