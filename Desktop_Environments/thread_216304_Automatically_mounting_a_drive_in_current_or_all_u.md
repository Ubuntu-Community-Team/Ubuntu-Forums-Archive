---
title: "Automatically mounting a drive in current or all users home dir"
date: 2006-07-15
forum: Desktop Environments
---

### Post by red_Marvin on 2006-07-15
I want to have all my family's photos on a second drive so it won't be affected as easily by my computer tinkering etc. But I do also want it easily accessible for all users (= not /mnt/photo but rather ~/photo)

I have checked the man page for fstab but haven't reached a solution since I want it mounted in many places (= /home/user1/photo and /home/user2/photo) at the same time or a mount point that's moving depending on which user is logged on (= user1 logs in: mount drive in ~, logs out: umount drive)

Any suggestions on how to automate this is welcome.

Oh, and I suppose I'll have to chown or chmod the files at logout or something, so that the next user logging in will have no problem accessing the photos when he/she logs in.

---

### Post by infoburner on 2006-07-15
try this:
```

ln -s /mnt/photo /home/user/photo

```
then as long as the drive is mounted as usual to /mnt/photo, the user will see it in their ~/photo directory

---

### Post by red_Marvin on 2006-07-15
So I create an entry for the drive in fstab as and then make links to each user. sounds good

Any ideas on how to fix permissions/ownership?

---

