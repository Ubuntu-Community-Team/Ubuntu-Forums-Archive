---
title: "Some applications can't see windows partitions"
date: 2009-03-02
forum: General Help
---

### Post by Zirconic on 2009-03-02
Some applications (ex: Amarok and KeepassX) can't see Windows partitions while others can (ex: OpenOffice and Evolution).  Is there a fix or is this an application by application issue?

Thanks in advance!

---

### Post by geirha on 2009-03-02
It's because amarok is kde-based, and does not have the ability to access gnome virtual filesystem. Kde has a similar set up, and gnome-based applications won't be able to see the drives when running on kde either. When a filesystem is mounted though, it will be accesible through /media/LABEL (Filesystem -> media -> LABEL) where LABEL is the label of the filesystem. If it does not have a label, a generic mount-point is chosen; /media/disk, /media/disk-1, /media/disk-2 etc. the first one available at the time it is mounted.

---

### Post by Zirconic on 2009-03-02
Thanks for the quick response geihra.

I navigated to filesystem/media/LABEL and found the drive I mounted.  If I understand this correctly, even if a drive is mounted contents won't be viewable because the gnome/kde issue trumps the mounted drive issue.

The solution appears simple: stick with kde or gnome-based applications to match my environment.

---

### Post by geirha on 2009-03-02
If it is mounted, you can always access it by browsing to /media/LABEL, it just won't show up with the convenient harddrive icon in the left-margin if the application does not support gnomevfs.

---

