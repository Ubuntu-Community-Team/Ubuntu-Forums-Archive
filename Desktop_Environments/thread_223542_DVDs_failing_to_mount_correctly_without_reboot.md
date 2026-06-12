---
title: "DVDs failing to mount correctly without reboot"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Quitch on 2006-07-26
I could have sworn this was working on my virgin Breezy install and only started having problems after the Dapper upgrade.

Anyway, I insert a DVD (I've tried several) and the drive spins for a moment, then stops.  No icon appears on the desktop to indicate the disc is mounted.

I open Places - Computer and choose to mount the DVD drive.  I get the following error:

[i]mount: block device /dev/hdb is write-protected, mounting read-only
mount: /dev/hdb already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdb is already mounted on /media/cdrom0[/i]

Indeed, it appears that I have a working /cdrom folder in the filesystem.

Of course, now if I open Totem Movie Player to play the disc, I can load it if I open /cdrom, but not using Play DVD.  In fact if I do that the disc is ejected because it's unable to mount /dev/hdb

Yet if I reboot the machine, I now have an icon on the desktop to indicate the mounted disc and everything seems to work as expected, with icons appearing and disappearing for mounted discs and the Play DVD option in Totem working as expected.

What's going on?

---

