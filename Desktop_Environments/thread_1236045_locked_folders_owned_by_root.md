---
title: "locked folders owned by root"
date: 2009-08-09
forum: Desktop Environments
---

### Post by bgmomof2 on 2009-08-09
Ok, here's one for you... I have many folders that were create by photorec to recover files from a repartitioned drive.  The folders are on my Ubuntu 9.04 64 bit system.  I can't get to locked folders that are owned by the root.  How do I sign in as root to edit the folders?  I am not too experienced at command line, although I have searched for the correct commands.  HELP me unlock these folders please.

---

### Post by merlinus on 2009-08-09
```
gksu nautilus
```

will give you root privileges.

---

### Post by Narada on 2009-08-09
Try running this on the directories in question:
```
sudo chown -R yourname directory
```
That should assign ownership to you and hopefully allow you to access the files.

---

### Post by bgmomof2 on 2009-08-09
Thanks for the help. I now have access.  gksu nautilus worked.

---

