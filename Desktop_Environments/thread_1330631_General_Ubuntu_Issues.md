---
title: "General Ubuntu Issues"
date: 2009-11-18
forum: Desktop Environments
---

### Post by alfu on 2009-11-18
[COLOR="SlateGray"]*Ubuntu will likely never become mainstream if users have to fiddle with the Terminal, so items here relate only to operating a computer via the GUI.  Though there is no 'About Gnome' dialog available from the desktop, I assume that is what it is running.    At present these apply to 9.04 due to stability issues with 9.1.*
[/COLOR]

**Drive Identification:** I can find no way to determine what physical drive a partition is on from opening its Properties dialog.  I can find many Emblems to use, which I consider cutsie, but fairly useless.

**Drive Label:** I can find no way to name a partition without going into GPartEd.

**Permissions in writing to external disks:** I have a large external USB drive formatted into multiple partitions.  Most of the time all of the partitions mount but I can't write to them because only ROOT has permission to do so.

If the user can't write to a partition, it should not mount in the first place.  It would also be nice to be able to set 'mount/do not mount' flags in each partition to keep the drive from flooding the desktop with windows when the drive starts up.

---

### Post by karlson on 2009-11-18
> **alfu said:**
> [COLOR="SlateGray"]*Ubuntu will likely never become mainstream if users have to fiddle with the Terminal, so items here relate only to operating a computer via the GUI.  Though there is no 'About Gnome' dialog available from the desktop, I assume that is what it is running.    At present these apply to 9.04 due to stability issues with 9.1.*
[/COLOR]

Can't say I agree with this statement.  There is something to be said about privileges the original UNIX philosophy etc, but this is a philosophical discussion that can be had in a different thread in a different forum.  

> 
**Drive Identification:** I can find no way to determine what physical drive a partition is on from opening its Properties dialog.  I can find many Emblems to use, which I consider cutsie, but fairly useless.

**Drive Label:** I can find no way to name a partition without going into GPartEd.

Have you looked at Webmin for all these?

> 
**Permissions in writing to external disks:** I have a large external USB drive formatted into multiple partitions.  Most of the time all of the partitions mount but I can't write to them because only ROOT has permission to do so.

If the user can't write to a partition, it should not mount in the first place.  It would also be nice to be able to set 'mount/do not mount' flags in each partition to keep the drive from flooding the desktop with windows when the drive starts up.

If you are the only user on the system you could potentially login as root and read and write any and everything you please.  In nautilus you go to Edit->Preferences to configure what happens with the external drives when they are connected as the OS itself doesn't do anything to mount unless it is configured in /etc/fstab.

---

