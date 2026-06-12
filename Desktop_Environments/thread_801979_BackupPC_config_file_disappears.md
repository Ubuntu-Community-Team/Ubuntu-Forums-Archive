---
title: "BackupPC config file disappears"
date: 2008-05-21
forum: Desktop Environments
---

### Post by best.nose on 2008-05-21
Hi there

I have been using backupPC for 6 months or so. Currently I am running the version that is in the repos for Ubuntu 8.04 (version 3.0.0). Recently I have been getting an error telling me that "No files dumped for share C". This is because it is defaulting to the config.pl file as my localhost file (called localhost.pl is not there!

This has happened about 3 times over the last month or so. So far, i solve the issue by getting the file from a previous backup, copying and changing permissions of the restored file so that backups can resume normally. The last time I did this I made the file read only for the owner (backuppc) with no other permissions associated with the owner or group (root). I assume the root user must be deleting the file if this is the case.

Has anybody got any suggestions regarding tracking down what is going on, ie what process is deleting this file?

Any help would be greatly appreciated!

Cheers

---

