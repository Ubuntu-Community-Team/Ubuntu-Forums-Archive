---
title: "backup util"
date: 2006-07-31
forum: Desktop Environments
---

### Post by frente69 on 2006-07-31
I want to backup from my ubuntu server to a windows pc at regular times.

What is the backup program of user friendlyness choice that i should use? 
Does it have the ability to run at regular times and does it have the ability to store a username and password to gain access to the windows share?

---

### Post by aysiu on 2006-07-31
I've never backed up to another computer on a network before, but I know KDar is a pretty good graphical utility for backups.

I prefer using *rsync* (for which there is a graphical frontend called *grsync*). ```
rsync -av /directory/to/be/backed/up /windows/share
```

---

### Post by adamkane on 2006-07-31
You can try sbackup. It is a GUI for tar. Allows you to include/exclude files/directories that you want to backup.

---

