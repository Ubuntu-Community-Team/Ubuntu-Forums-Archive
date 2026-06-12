---
title: "Cannot write to partation as a user."
date: 2009-04-18
forum: General Help
---

### Post by dE_logics on 2009-04-18
I want my account to be able to write to a mounted partition...what should I do?

Till now only root can do that.

---

### Post by juancarlospaco on 2009-04-18
Perfect, its normal.

Change Owners on this partition.

---

### Post by dE_logics on 2009-04-18
How?

---

### Post by juancarlospaco on 2009-04-18
sudo chown $USER /media/yourpartitionnamehere/

---

### Post by atomizer on 2009-04-18
```
sudo chown -R you /path/to/partition
```

---

### Post by dE_logics on 2009-04-18
Ok thanks, but can I set the mount options such that any user can write on it?

---

### Post by justin_guerin on 2009-04-18
> **dE_logics said:**
> Ok thanks, but can I set the mount options such that any user can write on it?

Yes, but how to do so depends on the format of the partition you want to mount.  If it's ext2/3/4, the rights are defined in the file system you're mounting, so if you can't read / write the files as the user in question, you'll have to elevate your access.

If it's a vfat partition, you can use the uid and gid directives to set the owner / group of the mounted partition.

See the mount man page for more details.

---

### Post by dE_logics on 2009-04-18
Ok...thanks a lot people.:)

---

