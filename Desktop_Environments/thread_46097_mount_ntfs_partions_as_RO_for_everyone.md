---
title: "mount ntfs partions as RO for everyone?"
date: 2005-07-03
forum: Desktop Environments
---

### Post by darkpark on 2005-07-03
Hello,

I have two ntfs partions that i have setup in fstab and they successfully mount but are only accessible for the root account.  
I'd like to have those two partitions mounted as read-only and readable for everyone local.  what should my two lines in fstab look like?  currently, they are as ...

/dev/hda5     /drive_e    ntfs,ro,umask=0222    
/dev/hdb1     /drive_d    ntfs,ro,umask=0222    

can you help?

---

### Post by Xian on 2005-07-03
Here's what I use:
```
/dev/hda1  /ntfs  ntfs  ro,users,gid=users,umask=0002,nls=utf8 0 0
```

---

### Post by darkpark on 2005-07-03
thank you.  that worked like a charm. :)

---

