---
title: "Software center problem"
date: 2012-01-03
forum: Desktop Environments
---

### Post by arockiyaselva on 2012-01-03
I have Ubuntu 10.10. My software center works fine until i change the permission of /usr. Now when i tried to install something using software-center, the authendication window shaked and closed immediately.How can i fix that problem?

---

### Post by mcduck on 2012-01-03
Change the permission of /usr back to what it's supposed to be. And if you changed the permissions recursively (all contents instead of just /usr itself) try to trace back the correct permissions for each file.

Changing ownership or permissions of system directories is a pretty sure way to break your system. The ownerships and permissions are what they are for good reasons and you really shouldn't mess with them unless you are absolutely sure it's required and you know what you are doing.

---

### Post by arockiyaselva on 2012-01-08
Yes. You are absolutely correct, but I dont know the default permission value for /usr. Does anyone knows that?

---

### Post by arockiyaselva on 2012-01-08
Where i can found that(default permission values)???

---

### Post by bluexrider on 2012-01-08
You could probably get started by or in which most of the applications or directories right underneath /usr are all owned by root and are  rwxr-xr-x for thier permissions except the /usr/bin and /usr/sbin  directories which are owned by root and group owned by bin, with the  same permissions.
Any links within /usr are usually rwxrwxrwx and owned by root.

That should get you started and it should mostly be the same throughout, etc.

---

### Post by bluexrider on 2012-01-08
> **arockiyaselva said:**
> Where i can found that(default permission values)???

```
ls -al /usr
```

this will show the permissions and the files listed in /usr

---

