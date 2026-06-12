---
title: "Where is the mount point?"
date: 2009-07-23
forum: Desktop Environments
---

### Post by RunningBear on 2009-07-23
When mounting a remote file system using the file manager, the remote system shows up in the left hand column of the file manager window.  Some applications can find the remote system just fine.  Others, such as "Back in Time" cannot.  I cannot find the mount point for the remote system.  Where might it be?

Thank You

_DAVID WARNER

---

### Post by ibutho on 2009-07-23
Have you looked in /media and in /mnt? Thats usually where filesystems are mounted.

---

### Post by RunningBear on 2009-07-25
I have looked in /media and /mnt and it is not there.  Any other suggestions?

Thanks

---

### Post by oldos2er on 2009-07-25
**mount -l** will show all mount points on a given system.

---

### Post by RunningBear on 2009-07-25
I have tried that.  The remote file system does not show up using mount -l.  It does appear in the left hand column of the file manager and the files are accessible directly (that is, clicking on one will cause it to open in the appropriate application.  However, not all applications will show the remote file system in their open dialogs.  Any other ideas as to what is going on and how I can make the remote file systems accessible from all applications?  I really would like to use "Back In Time" to store backup copies on the remote system, but I cannot access those resources from "Back in Time".

Thank You
_DAVID WARNER

---

