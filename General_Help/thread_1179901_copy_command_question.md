---
title: "copy command question"
date: 2009-06-06
forum: General Help
---

### Post by yoma819 on 2009-06-06
Dear all
i am looking to copy a complete directory from point a to point b!
it is about 18 gig so i need to leave it overnight!
the only problem is that every so often it pops up with a unreadable file.
that is not a problem other than i am not there to click skip!
is there some way to use the CP command to copy the folder and all files in it from 
/mount/12/backup
to 
/home/user/restore
help please!
many thanks
yoma

---

### Post by yoma819 on 2009-06-06
bump

---

### Post by Poyntz on 2009-06-06
Have you tried 
```
sudo cp -f /mount/12/backup /home/user/restore
``` ?
To copy the folder

Someone please correct me someone if I'm wrong.

---

### Post by Idefix82 on 2009-06-06
> **Poyntz said:**
> Have you tried 
```
cp -f <the folder you want to copy>
``` ?


I think this command is for when a destination file that needs to be overwritten cannot be opened, not when a source file is unreadable.

Why are the source files unreadable? Because you don't have the permissions?

---

### Post by ActiveFrost on 2009-06-06
Try this :
```
sudo cp -rf /mount/12/backup /home/user/restore
```

---

