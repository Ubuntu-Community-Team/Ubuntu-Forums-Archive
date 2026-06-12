---
title: "Cannot access my home folder in any application"
date: 2008-12-07
forum: General Help
---

### Post by tmastran on 2008-12-07
Any program that tries to access my home folder hangs. ls -lA from a command window just hangs. ls -lA from a command window as root on my home folder gives:

ls: cannot access .gvfs: Permission denied

This is just bizarre! I have read many threads talking about gvfs and fuse, but none that explain why I cannot access my own home folder or how to fix it?

Are there some diagnostic commands I can run to troubleshoot? Does some process have some kind of lock on something in my home folder? Accessing files in your own home folder should just work. This just about makes the system unusable.

I am running Gnome on Ubuntu 8.10.

Thanks,
Ted

---

