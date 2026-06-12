---
title: "Unity crashes/reloads after second Truecrypt volume is mounted within home directory"
date: 2012-11-04
forum: Desktop Environments
---

### Post by temmokan on 2012-11-04
Hello,

Ubuntu: 12.04, 64-bit, standard installation.

I am using several truecrypt-encrypted volumes (one as an encrypted disk partition, the other a file container) and noticed that is the following is performed:

1. Partition volume is mounted outside current user's home directory
2.  File container volume is mounted within current users' home directory

sample commands (using the Truecrypt CLI version downloaded from its official site):

```
sudo truecrypt /dev/sdc3 /local
sudo truecrypt ~/volumes/disk.dat ~/mount/volume

```

the following happens *almost* always:

- a file manager (Nautilus) window opens for the file container mounted at the second step
- Nautilus reports a fatal error and suggests restarting it
- the entire GUI (Unity) is reloaded

After that, no further errors related to the volumes happen.

If I reverse the order in which I mount the two volumes, Nautilus window doesn't pop up and no errors happen.

Is it a known problem? How do I know for sure which piece of software (Gnome, Unity. Nautilus) it is generated in and how shall I report the bug?

Thanks.

---

