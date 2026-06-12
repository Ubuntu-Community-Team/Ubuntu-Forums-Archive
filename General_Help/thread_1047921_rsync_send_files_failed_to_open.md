---
title: "rsync: send_files failed to open"
date: 2009-01-22
forum: General Help
---

### Post by kennyschiff on 2009-01-22
I've set up Grsync and run it, and it fails to complete. Here's the output from rsync. The user running Grsync is the owner of NAS. 

*** Launching RSYNC command:
rsync -r -t -v --progress --delete --ignore-existing /media/NAS/ /media/USBBackup/

sending incremental file list
rsync: send_files failed to open "/media/NAS/.journal": Permission denied (13)

sent 2101945 bytes  received 5743 bytes  383216.00 bytes/sec
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
total size is 453730398412  speedup is 215273.99

---

