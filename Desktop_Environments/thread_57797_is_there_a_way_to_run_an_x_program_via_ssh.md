---
title: "is there a way to run an x program via ssh?"
date: 2005-08-17
forum: Desktop Environments
---

### Post by nbx909 on 2005-08-17
anyway to run any x program through ssh? for example xchat? on a windows machine?

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=nbx909]anyway to run any x program through ssh? for example xchat? on a windows machine?[/QUOTE]
Yes.
On windows, you need an ssh client an an X display server.  You connect to the remote machine with the ssh client with X forwarding enabled.

For example, with cygwin on the Windows machine:
```
$ ssh -Y -l myusername remotemachine
Password:
myusername@remotemachine$ gedit
```

Cygwin has a free X server for windows.  I like using TopologiLinux for this purpose.  Commercial packages like Hummingbird Exceed exist as well.

---

