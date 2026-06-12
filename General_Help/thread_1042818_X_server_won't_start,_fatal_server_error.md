---
title: "X server won't start, fatal server error"
date: 2009-01-17
forum: General Help
---

### Post by GCFreak on 2009-01-17
It USED to work, but now, without touching anything it just doesn't.

After it drops me to a shell and I try to start the X server with xinit, it outputs this:

```
X: warning: process set to priority -1 instead of requested priority 0

Fatal server error:
Could not create lock file in /tmp/.tx0-lock

giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

I have searched other threads that have had this problem, and their solutions haven't fixed it here.

Thanks in advance.

---

### Post by lensman3 on 2009-01-17
Make sure that /tmp directory exists and is owned by root and of group root.

AND 

file permissions for the dot file are: drwxrwxrwt

Don't forget the trailing "t".

chmod 777 /tmp
chmod ugo+t /tmp

See if that works.  Your error messages indicate (to me) that /tmp didn't exist and you didn't have permission to use it.  The trailing "t" has to do with restrictive permissions on a created file in a world accessible directory.  (That is, when you create a file in a world readable directory, then only the creator can read the file.   Disallows snooping as I remember).

Hope this helps.

---

