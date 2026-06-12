---
title: "kubuntu memory stick case sensitivity"
date: 2008-03-17
forum: Desktop Environments
---

### Post by awry on 2008-03-17
I realized today that I can't properly sync my memory stick using kubuntu's default mount options for vfat.  When I plug in the memory stick, it gets mounted with the 'shortname=lower' option.  This forces all 8.3 file/folder names to be converted to lowercase when written to the vfat volume.  (See 'man mount' for details.)

In Bug 15225, the ubuntu team decided that the default for (at least the gnome distro) should be 'shortname=mixed'.  I don't know if kubuntu never followed this lead, or if I'm seeing a bug/regression.

Is there somewhere in kubuntu where I can tell it to mount the volume with 'shortname=mixed' instead of 'shortname=lower'?  It's a real PITA to umount/remount the thing every time I want to sync my files.

I filed bug 203321 on this issue.

---

