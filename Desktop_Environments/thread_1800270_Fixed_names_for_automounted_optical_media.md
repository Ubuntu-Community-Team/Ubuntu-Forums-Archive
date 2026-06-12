---
title: "Fixed names for automounted optical media"
date: 2011-07-08
forum: Desktop Environments
---

### Post by fmouse on 2011-07-08
I'm running Ubuntu 11.04 on a desktop box, and need the automount system to generate a mountpoint name in /media based on the drive unit rather than the volume name of an inserted CD or DVD.  On inserting any media in the first DVD-R drive, it should be automounted as, e.g., /media/op-drive0 instead of /media/<volume_name> as is now the case.

I have an older, Gentoo box, on which I created a hal config file along the lines of the instructions at [https://bbs.archlinux.org/viewtopic.php?id=91450](https://bbs.archlinux.org/viewtopic.php?id=91450) but I can't get this to work on this box.  Other instructions say to use gnome-mount but Ubuntu doesn't seem to know about this utility.

Any suggestions would be appreciated.

---

