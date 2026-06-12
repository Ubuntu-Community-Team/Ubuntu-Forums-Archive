---
title: "need help removing a directory"
date: 2009-05-16
forum: General Help
---

### Post by boondocks on 2009-05-16
In a user's home directory, doing "ls -al" shows:

```
...
drwx------  2 goofy goofy    4096 2009-05-15 20:25 .gnupg
drwxr-xr-x  2 goofy goofy    4096 2009-03-20 21:07 .gstreamer-0.10
-rw-r--r--  1 goofy goofy     120 2009-05-15 20:25 .gtk-bookmarks
d?????????  ? ?     ?           ?                ? .gvfs
-rw-------  1 goofy goofy   11162 2009-05-15 20:25 .ICEauthority
drwxr-xr-x  2 goofy goofy    4096 2008-05-11 16:49 .icons
...

ls: cannot access .gvfs: Permission denied

```
Even with sudo, I cannot remove this ".gvfs"
How do I get rid of it?

---

### Post by albinootje on 2009-05-16
> **boondocks said:**
> 
ls: cannot access .gvfs: Permission denied
[/CODE]
Even with sudo, I cannot remove this ".gvfs"
How do I get rid of it?

.gvfs is some special Gnome Virtual File System directory.
Leave it, and ignore it.

---

