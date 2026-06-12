---
title: "Why Gnome VFS and not LinNeighborhood?"
date: 2006-12-05
forum: Desktop Environments
---

### Post by xp_newbie on 2006-12-05
Why does Ubuntu use the Gnome VFS and instead of integrating the LinNeighborhood into the Gnome desktop in order to connect to Samba/Windows network shares?

The reason I am asking is that many Linux applications do not (or cannot) work with Gnome VFS, but rather need a "traditionally mounted point". This is especially true for legacy applications (both command line and X11), which are still very useful.

I found the LinNeighborhood package providing exactly what I need from a Linux desktop accessing Samba shares:
[LIST=1]
[*]Access by **all** applications.
[*]Mount on demand (just as in Gnome VFS). That is, not having to use fstab which mounts shares even before any user logs in.
[*]Mount on demand (just as in Gnome VFS). That is, not having to embed passwords in a credentials file (in clear text, which is not very secure).
[/LIST]
Any idea whether there any plans to have LinNeighborhood (or similar) replace the Gnome VFS in the nice "Places" menu on the top panel?

Thanks,
Alex

---

