---
title: "Gnome Automount Permissions"
date: 2010-08-01
forum: Desktop Environments
---

### Post by needhelppeeps on 2010-08-01
Gnome automounts my external USB which is great, but the problem is I am not given read/write permissions which is driving me crazy. I have to read/write as root instead of the currently signed in user. I looked under gconf-editor but didnt find any storage settings, I also dont seem to have anything relevant under preferences. Anyone know where these settings are hidden?

---

### Post by sikander3786 on 2010-08-01
Hi.

Which File System on the external USB? I assume it is not FAT.

---

### Post by needhelppeeps on 2010-08-01
Ext3. Slight mistake in my OP, It should say user has read permission, but only root has write permission

---

### Post by hakzsam on 2010-08-01
```
man mount
```
It should be a good issue for your problem.

---

