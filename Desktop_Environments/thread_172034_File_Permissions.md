---
title: "File Permissions"
date: 2006-05-07
forum: Desktop Environments
---

### Post by GuitarHero on 2006-05-07
Everytime I copy music from my external hard drive to my ubuntu hard drive the permissions are set to read and execute, not write.  How do I get it to copy them with full permission settings?

---

### Post by Gannin on 2006-05-07
What file system is your external hard drive formatted with?

---

### Post by GuitarHero on 2006-05-07
not sure but i think it is ntfs

---

### Post by Sutekh on 2006-05-07
If the partition is NTFS, then the permissions of the files *on* the partition will likely be read and execute.  Without extra alterations, you won't be able to set your files on the NTFS partition to have write permission.

When you copy them over the permissions will remain.  You will have to change them if you need the write permission bit.

If you can, copy them across in one folder, and use this command to add the write permission bit to all the files (including those in sub-folders)
```
sudo chmod +w -R /<path of copied files>/
```

---

