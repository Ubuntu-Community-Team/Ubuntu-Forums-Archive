---
title: "unable to boot ubuntu after installing windows."
date: 2009-01-16
forum: General Help
---

### Post by yobird42 on 2009-01-16
I shrunk down my ubuntu partition and installed windows xp on the remaining space. After the installation, it went straight into booting xp without going to the grub loader

I booted into the intrepid alpha release I had laying around and typed in this command to restore the MBR backup I made, however nothing happened. 

```
dd if=/dev/sda/mbr_backup of=/dev/sda1 bs=446 count=1
```

How do I make it so that grub comes up before windows?

---

### Post by taurus on 2009-01-16
Maybe this link helps, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

