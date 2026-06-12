---
title: "directory has no permissions, owner or group, and root can't do anything to it"
date: 2009-04-23
forum: General Help
---

### Post by sgorczyca on 2009-04-23
I noticed this problem while using rsync to backup to our NAS device.
The problem directory is /usr/local/backup

here's an output of ls -alh /usr/local:
```

drwxr-xr-x 14 root root 4.0K 2009-04-04 12:19 .
drwxr-xr-x 12 root root 4.0K 2009-01-27 13:15 ..
d?????????  ? ?    ?       ?                ? backup
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 bin
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 etc
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 games
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 include
drwxr-xr-x  4 root root 4.0K 2009-01-27 11:01 lib
lrwxrwxrwx  1 root root    9 2008-02-14 09:56 man -> share/man
drwxr-xr-x  2 root root 4.0K 2009-04-04 12:19 oakmont
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 sbin
drwxr-xr-x 13 root root 4.0K 2009-02-19 13:11 share
drwxr-xr-x  4 root root 4.0K 2009-04-04 13:19 software
drwxr-xr-x  2 root root 4.0K 2008-02-14 09:56 src
drwxr-xr-x  4 root root 4.0K 2008-02-15 12:32 svn

```
Logged in as root, i can't do anything to this file.  I can't chmod, chown, chgrp, ls, rm or cp it, root gets permission denied for any action regarding this file.  Does anyone have any idea what happened here, or have any suggestions for further troubleshooting?

---

### Post by Tobi-fp on 2009-04-23
If i were you id snap a bootcd from [www.hiren.info](www.hiren.info)
That cd has got it all, if anything can fix your directory, its hirens boot cd ;)

Hope it helped

---

### Post by sgorczyca on 2009-04-23
I'll give that a try over the weekend if I can't find any other way to fix it.  I'm hoping to avoid rebooting the system, since it's the server running our issue tracking software.

---

### Post by sgorczyca on 2009-04-23
Ok, we figured it out.  The directory was actually a mount point for a broken NFS mount.  umount /usr/local/backup fixed the problem.  Now we've just got to figure out who created an nfs mount there and why.

---

