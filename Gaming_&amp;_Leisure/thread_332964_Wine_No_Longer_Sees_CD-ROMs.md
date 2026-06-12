---
title: "Wine No Longer Sees CD-ROMs"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by infidel on 2007-01-06
Sorry to bother everyone with this, but I've been through every HOW-TO and forum post I can Google and all indications are that I have everything properly configured. Still, games I have installed under Wine (v0.9.22 under Edgy) have stopped being able to see CD-ROMs.

My CD-ROM drive is /media/cdrom0, and is mounted. My ~/.wine/dosdevices looks like this:
```
lrwxrwxrwx 1 marv marv 10 2006-08-09 19:48 c: -> ../drive_c
lrwxrwxrwx 1 marv marv 13 2006-08-09 19:49 d: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  9 2006-10-31 20:55 e:: -> /dev/sde1
lrwxrwxrwx 1 marv marv 13 2007-01-06 14:58 g: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  8 2006-11-26 22:31 g:: -> /dev/hdc
lrwxrwxrwx 1 marv marv 10 2006-08-09 19:50 h: -> /home/marv
lrwxrwxrwx 1 marv marv  1 2006-08-09 19:48 z: -> /
```

Running 'winecfg' and clicking on the 'Drives' tab, my drives are mapped as follows:

C:  ../drive_c
D:  /media/cdrom0
G:  /media/cdrom0
H:  /home/marv
Z:  /

And here's my fstab, if it matters:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=c4ade41c-9d07-4cd2-b40c-b32d70d4c342 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=063bbf67-3220-4a28-8c0d-6700198d2430 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Every time I try to run an installed game, I get a message that there is no disc in the drive. Even when I try to run a game's autorun from the disc itself, I get the standard splash screen and then the error. Odd (to me) that Wine will run the autorun from the disc which it subsequently insists is not present.

I haven't done anything with Wine for weeks, and can't recall anything I've done system-wise which might have interfered with Wine's config.

Basically, I'm completely stumped. What am I overlooking? Any and all help would be greatly appreciated; many thanks in advance.

---

### Post by Enverex on 2007-01-10
Delete....

lrwxrwxrwx 1 marv marv 13 2006-08-09 19:49 d: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  9 2006-10-31 20:55 e:: -> /dev/sde1
lrwxrwxrwx 1 marv marv 13 2007-01-06 14:58 g: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  8 2006-11-26 22:31 g:: -> /dev/hdc

As they are probably conflicting with each other. Also go into winecfg afterwards and make sure they are removed from there too.

---

### Post by infidel on 2007-01-10
> **Enverex said:**
> Delete....

lrwxrwxrwx 1 marv marv 13 2006-08-09 19:49 d: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  9 2006-10-31 20:55 e:: -> /dev/sde1
lrwxrwxrwx 1 marv marv 13 2007-01-06 14:58 g: -> /media/cdrom0
lrwxrwxrwx 1 marv marv  8 2006-11-26 22:31 g:: -> /dev/hdc

Thanks, Enverex. 

I deleted them from the command line without incident, but the mere act of running winecfg remade them. However, noticing that my Windows version was set to 98, I changed it to XP and now cdroms work just fine.

I'm guessing that the games in question were installed with Wine faking an XP install (can't remember; like I said, it's been weeks). I'm not sure how my drive got duplicated.

At any rate, everything appears to be fine for now. Thanks again.

---

### Post by Enverex on 2007-01-11
Ack, glad it worked but for future reference install the apps inside Wine rather than copying them over from an existing install (some games may need DLLs and Regsitry entries to be installed).

---

### Post by infidel on 2007-01-11
> **Enverex said:**
> Ack, glad it worked but for future reference install the apps inside Wine rather than copying them over from an existing install (some games may need DLLs and Regsitry entries to be installed).

Sorry; you may have misunderstood me. There were no existing installs other than with Wine. I don't do Windows. :)

Thanks again!

---

### Post by Enverex on 2007-01-11
Ah sorry, misinterpreted how it was written. Good luck then.

---

