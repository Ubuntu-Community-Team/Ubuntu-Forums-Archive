---
title: "can't cd to ntfs partition due to permissions"
date: 2006-04-21
forum: Desktop Environments
---

### Post by ofelman on 2006-04-21
i have loaded 6.06 beta on a laptop with an existing ntfs partition (hda1) which seems to be mounted under /media/hda1... however, when i try to cd to /media/hda1 or browse to it, it get an error suggesting i do not have permissions to get to the file system

am i missing something?

---

### Post by aysiu on 2006-04-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by daageep on 2006-04-21
i had that problem before. use the command "id" and see see what your uid is. mine is "uid=1000(vorganna)", so its 1000. in /etc/fstab, add uid=1000 in options for your ntfs partition.

mine is "/dev/hda1 /mnt/windows ntfs user,auto,uid=1000 0 0"

just remount, and it *should* work. =)

---

### Post by louis_nichols on 2006-04-21
entering in fstab

```
/dev/hda1 /mnt/windows ntfs users,auto 0 0 
```

would also do the trick. perhaps even better, since all users will then be able to access it.

---

