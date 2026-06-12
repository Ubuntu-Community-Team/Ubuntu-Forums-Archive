---
title: "How to mount ext3 partition and r/w by no root user"
date: 2006-08-09
forum: Desktop Environments
---

### Post by eyess on 2006-08-09
my fstab contents is as follows:

/dev/hda3       /data           ext3    defaults,user        0       0
/dev/hda4       /work           ext3    defaults,user        0       0

after turn on,mount these partition is good,but no-root user isn't write right!

how to mount these partition after PC was turn on,and no-root user have R/W
right?

help me ?

---

### Post by hopstah on 2006-08-09
i changed the owner and the group of my mounted ext3 drives to make me the owner and group of them, giving myself full permissions to them
```
sudo chown (name) (drive)
sudo chgrp (name) (drive)
```

---

### Post by scxtt on 2006-08-09
hopstah is on the right path, so as long your user owns the directory that you're mounting to, you'll own all new files created there (and you can give the folder -rwx---rwx properties so others can (if you want) ...

anything mounted @ boot will be mounted as root, so i'd remove the lines from /etc/fstab if you don't want that to happen ...

---

### Post by eyess on 2006-08-11
what is mean?

---

### Post by hopstah on 2006-08-11
> anything mounted @ boot will be mounted as root, so i'd remove the lines from /etc/fstab if you don't want that to happen ..

not true.  the first time, yes, but once the ownership is changed, the folders will remain that way.  you can also perform a chown -R to recursively change every subfolder.  but don't remove the lines from fstab, that just complicates things by requiring remounting after boot.

---

### Post by hopstah on 2006-08-11
> **eyess said:**
> what is mean?

ok, open up a terminal and type this in: ```
sudo chown -R username /data
sudo chown -R username /work
```
but obviously change 'username' to your login name

---

### Post by scxtt on 2006-08-11
yeah, i was thinking more about "the first time" or if someone hasn't changed it yet {in the way you mention} ... i also seemed to be thinking more about mounting samba shares when i posted that then folders on the / F/S ...

personally, i like to mount things only when i need them, so my fstab is minimal ...

---

### Post by hopstah on 2006-08-12
i could see that as well, but i NEED my music about 98% of the time my computer is on, so that's obviously an auto-mount :)

---

### Post by eyess on 2006-08-13
lots of thank!

---

