---
title: "Input/output error when deleting files"
date: 2012-04-26
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-26
I cannot delete these files 
```
root@subhi-pc:/media/SOB7I/Wekanew# rm database 
rm: cannot remove `database': Input/output error
```

---

### Post by mörgæs on 2012-04-26
Please use a more informative thread title. I have changed it for you this time.

---

### Post by SeijiSensei on 2012-04-26
What filesystem is on the mounted device?  

If you run "mount", is the device listed as read-only "(ro)"?  If so, you need to run a filesystem check.  Unmount the device before checking.  If it's an ext2/3/4 filesystem, use fsck; if it's an NTFS or FAT drive, you need to use Windows chkdsk.

---

