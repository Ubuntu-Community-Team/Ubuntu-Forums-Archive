---
title: "Backing up home folder"
date: 2009-01-04
forum: General Help
---

### Post by preki on 2009-01-04
Hi all,

I 'm trying to back up a folder, preserving ownerships and permissions, and I've tried

sudo rsync -aS preki/* prekiBackup
sudo cp -a preki/* prekiBackup

but in both cases when I try

sudo diff preki prekiBackup

then I get listed as "Only in preki:" the files starting with . - i.e. neither of the above commands have copied the hidden files.

Can somebody please tell me what I'm doing wrong?

Thanks,

---

### Post by zvacet on 2009-01-04
Maybe [this]("http://psychocats.s465.sureserver.com/ubuntu/backup") will help you.

---

### Post by heindsight on 2009-01-04
In the commands you posted, the shell will expand
```
preki/*
``` to a list of the contents of the directory preki, but this list excludes any files or directories with names beginning with a . 

to see this in action, try doing ```
echo preki/*
```

If you just remove the * then either of those commands will work, for the initial backup, cp is probably a bit more efficient and for subsequent backups rsync will be more efficient since it only copies files that have changed...

---

### Post by jackmetal on 2009-01-04
+1 to remove the *

Either command should work then.

---

