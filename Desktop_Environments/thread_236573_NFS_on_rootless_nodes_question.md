---
title: "NFS on rootless nodes question"
date: 2006-08-14
forum: Desktop Environments
---

### Post by abergou on 2006-08-14
Hello,

I set up a heterogenous rootless cluster under Breezy badger and recently upgraded to Dapper Drake and have been having serious problems with it since.  The server boots up fine now (I had some minor problems with the hard drives, and the ethernet cards being detected in a different order from before), however when I tried to boot the nodes (via PXE boot) I encountered serious problems.

The first one, which I somewhat seemed to solve is that initially the nfs drives weren't being mounted in /etc/fstab - however adding a symlink to mountnfs.sh from init.d to rcS.d seems to solve that problem.

That lead to the bigger problem which is that nfs takes FOREVER to mount.  I know that portmapper needs to be started on the server and the nodes in order for nfs to work properly, however during the startup process when portmapper is launched by the init scripts it comes up with a very very strange error:

> Portmap: fork: no such device  done

I'm not sure what's going on with that, I tried to google for the error, but it came up with nothing useful.  I was wondering if anyone had any insight into why portmapper isn't launching or how to properly fix the slew of problems that I've been having.  Thank you!

---

### Post by abergou on 2006-08-15
bump

---

### Post by abergou on 2006-08-16
bump

---

### Post by eskaland on 2008-02-26
I am seeing exactly the same problem as you did.

Did you find a solution to this problem ?

Help would be greatly appreciated!!

---

