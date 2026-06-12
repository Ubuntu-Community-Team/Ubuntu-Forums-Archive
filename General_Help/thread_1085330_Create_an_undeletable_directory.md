---
title: "Create an undeletable directory"
date: 2009-03-02
forum: General Help
---

### Post by vaf on 2009-03-02
Is it possible to create a folder permission that users can read and write files/folders to, but not actually delete the folder. The content can be deleted, but just not that folder.

I have tried this (all as root):
[LIST=1]
[*]mkdir <dir>
[*]chgrp cdrom <dir>
[*]chgmod 1777 <dir>
[/LIST]

ls -l returns

drwxrwxrwt 2 root cdrom  4096 etc

The directory is shared on Samba, but I am still able to delete the directory. 

Any suggestion would be great. thanks

---

### Post by tad1073 on 2009-03-02
```
chmod +t foldername
```

Quoted from Ubuntu Kung-Fu

"When set on a folder, the sticky bit means that only
the owner of a file or subfolder within that folder can delete it
(although the owner of the folder itself will be able to delete the
file, as can root). The sticky bit is useful for folders where files are
shared, but the administrator doesn’t want users to be able to
delete any other user’s files. The sticky bit is indicated in file listings
by a t at the end of the permission listing (i.e. drwxrwxrwt),
and is set by typing chmod +t foldername. When applied to a file
within Ubuntu, the sticky bit is meaningless and is ignored.
NOTE Should you see a capital S or capital T within file listings,
instead of lower case letters, the execute permission hasn’t been
set for the relevant file or folder. Although SUID and sticky bits
normally rely upon the file/folder being executable, they don’t
automatically set it."

---

### Post by lykwydchykyn on 2009-03-02
Seems like you'd need to set the sticky bit on the directory that contains the directory you want to make undeletable, and then make that directory owned by root.  Making the directory itself sticky only affects the folders in it, I believe.

---

### Post by vaf on 2009-03-02
Still doesn't work!  I have the following 

ls -l

drwxr-xr-t 2 root cdrom ...

But Windows Xp Samba machine still able to delete it!

---

### Post by vaf on 2009-03-02
The directory that contains the directory is the mountpoint of a drive. How do I set permissions for the mountpoint directory?

---

