---
title: "Trash-1000 on NAS"
date: 2008-09-04
forum: Desktop Environments
---

### Post by maxcelpc on 2008-09-04
I have a network attached storage NAS acting as a file server. It has three shares, of which two have multiple user access and one is restricted to me only. The problem is that when I attach one of the multi-user shares, I get a continuously repeating message as follows:

```
CIFS VFS: Error 0xfffffff3 on cifs_get_inode_info in lookup of /.Trash-1000/files
```

preceeded by date/time information. Message updates every 4 seconds.

Looking at the .Trash-1000 folders with show hidden set, it appears empty, but if I try to delete it, as suggested in other postings, it says that the folder is not empty. Using ```
sudo rm -R
``` says that access is denied. Using
```
gksudo nautilus
``` and then looking at Properties|permissions shows that I own .Trash-1000 folder, but I cannot delete it.

I have even tried changing the access rights on the NAS to me only, but I still cannot delete it.

---

