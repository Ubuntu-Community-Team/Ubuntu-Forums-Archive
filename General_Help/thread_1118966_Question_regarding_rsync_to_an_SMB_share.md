---
title: "Question regarding rsync to an SMB share"
date: 2009-04-07
forum: General Help
---

### Post by SoCalChris on 2009-04-07
I've got an SMB share mounted, that I want to backup my digital photos to. I've got approximately 60,000 photos that are being synced between the two systems.

I've got the share mounted correctly, and can rsync to it. The problem is that it checks each file every time I attempt to rsync, with 60,000+ files, this takes several hours.

I'm guessing that it has to do with file permissions, since NTFS doesn't support them, and rsync is trying to set the permission on each file in the SMB share. Is there a way to avoid this?

This is how I'm calling rsync:
```
rsync -rtvO --progress --partial --delete-before --delete-excluded --exclude '.*' --exclude '*.db' /home/chris/Pictures/ /media/chris-desktop/SyncPics/
```

---

