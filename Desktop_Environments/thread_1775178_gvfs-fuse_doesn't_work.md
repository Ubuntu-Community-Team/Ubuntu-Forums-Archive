---
title: "gvfs-fuse doesn't work"
date: 2011-06-04
forum: Desktop Environments
---

### Post by mikaelstaldal on 2011-06-04
I have the gvfs-fuse package installed, and if I understand it correctly it should make GVFS mounts appear in ~/.gvfs.

However it doesn't, when I mount something with GVFS (e.g. my Canon digital camera using PTP), I can only access the files from Nautilus, not from command line.

I have a ~/.gvfs directory, but it remains empty.

What can be the problem?

---

### Post by Morbius1 on 2011-06-04
Perhaps you are not a member of the fuse group:
```
 sudo gpasswd -a your-user-name fuse
```
Then logoff and login again for the group change to take affect.

---

### Post by mikaelstaldal on 2011-06-04
I am member of the fuse group, and I can successfully use FUSE for other things, such as sshfs.

---

