---
title: "Mirror directory across drives"
date: 2008-08-23
forum: Desktop Environments
---

### Post by monikersupreme on 2008-08-23
I recently installed Hardy on an older desktop PC that is running a pair of old 80GB ATA drives with the operating system installed on the first drive and /home (mounted) on the second. 

I would like a means of mirroring a set of directories across each drive (to provide a redundancy in a transparent manner for important files in case either of the drives die)... 

Is there package that I can install that will provide this and is relatively user-friendly to configure (as I'm rather new to Ubuntu and Linux in general)?

Any advice would be much appreciated...

Thanks!

---

### Post by scotchfx on 2008-08-23
Try sbackup...

---

### Post by monikersupreme on 2008-08-23
So I think I've been able to figure this out... using sbackup and backing up into the default /var/backup directory (since this is already on the drive that I wish to backup to). 

I've been installing various mirroring/backup packages for the last couple hours and now I've discovered a /var/backup**s** directory (in addition to the /var/backup directory used by sbackup).

Is this directory important... can I get rid of it? I think it's associated with one of the backup tools I installed then got rid of... possibly "keep" although I'm not 100%... is there an easy way to figure this out?

---

### Post by darthyorik on 2009-01-14
Don't know if you have found your solution, given it has been some time since you posted. I suggest you take a look at mirrordir, rsync or even wget.

mirrordir or copydir sound like just the thing you are looking for. rsync and wget are probably better for remote use.

mirror is another option if you need something more

---

