---
title: "new release, new annoyances..."
date: 2008-11-01
forum: Desktop Environments
---

### Post by samwisefoxburr on 2008-11-01
Hello, I've installed 8.10 and love it, but there are a couple of new annoyances that I would like disabled, if possible.

I've attached a screenshot pointing them out.  The /media/Files folder is hosted from my NFS server and so I would like to disable the F-Spot Photo Manager thing at the top and I would like to know if it is possible to remove the eject button since I save most of my data directly to the server (torrents and the like) and want to avoid accidentally clicking it.  Disabling the ability to mount/unmount it at all from the GUI would work, too, since it is mounted/unmounted automatically from fstab.

Thanks!

---

### Post by samwisefoxburr on 2008-11-01
Well, I kind of solved the problem.  I uninstalled F-Spot (could of sworn that it was tied to a bunch of dependencies in GNOME and Ubuntu, but I guess that changed in this release).  Brasero then took over with the infobar, so I uninstalled that (never used that, either, and I can just use GNOME's build-in writer, anyway), so that took care of the infobar issue.  In regards to the eject button, I realized that because of the way I have the NFS mount setup in fstab only root can unmount it, so I don't have to worry about it being accidentally unmounted.

---

