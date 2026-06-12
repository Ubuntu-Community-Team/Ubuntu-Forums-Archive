---
title: "Boot problem because of LVM error"
date: 2009-05-26
forum: General Help
---

### Post by elektronaut on 2009-05-26
Hi,

my system won't boot anymore, apparently because the root fs is on a logical volume and lvm seems to have some problems.

Boot message is:
```

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

If I boot with the alternate install CD and choose to execute root in the aforementioned root volume, it gets mounted. But if I try to execute any of the LVM commands, like 'pvscan', I get this message ```
locking type 1 initialization failed
``` Though it's possible to run the commands with the option 'ignorelockingfailure', there isn't any locking file (which I could delete) in the directory mentioned in the lvm.conf file.

Any ideas what to do now?

---

### Post by elektronaut on 2009-05-28
It seems that the locking failure has disappeared, but it still won't boot. So it must be something else about LVM.

---

### Post by elektronaut on 2009-05-28
Solved. Apparently the initrd image was rewritten incorrectly for unknown reasons. 'sudo dpkg-reconfigure linux-image-`uname -r`' did the magic.

---

