---
title: "Backup with grsync : rename instead of deleting"
date: 2009-05-20
forum: General Help
---

### Post by _Narcisse_ on 2009-05-20
Hey everyone,

I'm using grsync to backup all my personal files and I realized that when I rename one or several folders in the source, my Home dir, and synchronize it with the backup, rsync delete all the files in the renamed directory *then* copy it again with its name changed.

Is there any way to tell (g)rsync to *rename* it for real instead of doing all this deleting-copying job ?

Thanks for your help.

---

### Post by _Narcisse_ on 2009-05-21
Anyone, please ...?

---

### Post by StuartN on 2009-05-21
> **_Narcisse_ said:**
> Is there any way to tell (g)rsync to *rename* it for real instead of doing all this deleting-copying job ?

Quite simply, no. There is no way for rsync to match the renamed file or directory with a previous backup with a different name.

If it is a lot of data then you could rename the folders / files in the backup copy before running rsync.

---

### Post by _Narcisse_ on 2009-05-26
Thank you, I'll do this.

---

