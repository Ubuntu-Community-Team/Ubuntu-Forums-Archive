---
title: "Timeshift and rsync"
date: 2020-09-08
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-09-08
Assuming Timeshift is just a GUI for rsync (appreciate btrfs is an option too) I am wondering what is actually compared when making snapshots or restoring a previously saved image.

Bearing in mind with Timeshift there is the ability to delete saved snapshots I am wondering what a subsequent restore would compare with.

Geoff

---

### Post by vanadium on 2020-09-08
On creating a new snapshot, rsync compares with the previous snapshot. Files that are still the same as in the previous snapshot, are hard linked. Files that have changed or that have been added, are copied over. The hard-linking causes data of an unchanged file to exist only once in the backup location. It is only the directory entry that makes it to the new backup: that directory entry points to the same data as in the previous backup. Therefore, only changed files occupy additional disk space.

On restoring a previous snapshot, files from that particular snapshot are copied back to the system folders. Files in the system folders that are not in the backup, are deleted.

---

### Post by Geoff_Lane on 2020-09-09
> **vanadium said:**
> On creating a new snapshot, rsync compares with the previous snapshot. Files that are still the same as in the previous snapshot, are hard linked. Files that have changed or that have been added, are copied over. The hard-linking causes data of an unchanged file to exist only once in the backup location. It is only the directory entry that makes it to the new backup: that directory entry points to the same data as in the previous backup. Therefore, only changed files occupy additional disk space.

On restoring a previous snapshot, files from that particular snapshot are copied back to the system folders. Files in the system folders that are not in the backup, are deleted.

If, for an easy example, four snapshots exist and the second is deleted.  How does the third snapshot reference files if the prior image (The second) has been deleted?

I can understand incremental backups but don't quite understand how one in a chain can be deleted.

Geoff

---

