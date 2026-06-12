---
title: "Nautilus says disk full, Analyzer says 140 GB free"
date: 2010-12-21
forum: Desktop Environments
---

### Post by psi36 on 2010-12-21
I have a problem on my installation of Ubuntu 10.10: it shows 0kb space remaining in nautilus. When I delete files (also out of Trash) it shows there is again space, but within minutes this free space is full again.

When I look in Disk Usage Analyzer it says there is 140 GB available and it is impossible that the complete partition of 190 GB is full.
But I cannot save or download anything anymore and the system is not very responsive. So it seems to act as if the disk is completely full.

Any idea what could be the problem?

---

### Post by oldfred on 2010-12-21
Post these:

```
sudo fdisk -l
```

```
df -H
```

Do you have a runaway error message that is filling up Log Files?
Check System, Administration, Log File Viewer and look at messages and other logs.

---

