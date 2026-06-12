---
title: "wont boot xp after linux hd removed"
date: 2009-02-03
forum: General Help
---

### Post by IceReaver75 on 2009-02-03
My cousin has a problem that maybe someone here can help sort out.  He had a computer running a xp and linux dual boot using 2 different hard drives.  He bought a new computer today and sold his old one to his parents.  He removed the hard drive with linux on it completely so he could use it in his new computer and left the xp drive in the one he sold.  He set the xp drive back to the master drive and when he got everything set-up at his parents house went to turn on the computer and it gave him a "unable to boot - grub error" message.  If the linux drive isn't in there at all any more how would he be getting a grub error message when booting?

---

### Post by fooman on 2009-02-03
should be able to fix by booting with the xp cd,  then entering the recovery/repair console.

from there,  type these 2 commands:
[COLOR=#0000c0]
[/COLOR]```

fixmbr
fixboot
```hope that helps.

---

