---
title: "Can't remove file"
date: 2009-05-22
forum: General Help
---

### Post by kahuna0789 on 2009-05-22
I am currently logged in as root trying to delete a file... but when I try to delete it, it fails and I get this error:

```
rm: cannot remove `./steam': Read-only file system
```the ls -l on this file comes out like this:
```
-rwxr-xr-x 1 16777218 16777216 6067624 2008-08-29 20:28 steam
```since i do not have a username called 16777218 I tried to chmod to give it 777 access and i tried to chown it to root:root and it says the command succeeds but when i ls again it is the same.

Is there anyway i can delete this file?

Thanks
Kahuna0789

Update: It was a disk consistency problem, after rebooting and running fsck i was able to delete the file,

---

