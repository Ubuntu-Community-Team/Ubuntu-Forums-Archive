---
title: "Windows partition broken? Grub error"
date: 2006-09-02
forum: Desktop Environments
---

### Post by mediocre on 2006-09-02
Hmmm... well, I just tried to boot to my windows xp home partition from the grub menu, and I get the message:

```
root  (hd0, 0)
  Error 24: Attempt to access block outside partition.
```

If it helps, the salient portion of /boot/grub/menu.lst is
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

and, from fdisk:
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/hda2            4865        5114     2008125   83  Linux
/dev/hda3            5115        5364     2008125   82  Linux swap / Solaris
/dev/hda4            5365       19457   113202022+   5  Extended
/dev/hda5            5365       12300    55713388+  83  Linux
/dev/hda6           12301       19457    57488571   83  Linux

Command (m for help): 
```  

So, before I go and do something foolish like try to re-install Windows, which will likely trash grub (?), I'd like to ask for some assistance.

N

---

### Post by mediocre on 2006-09-02
Just found another thread on this issue in which crashtestyyz reported (apparently) positive results by changing root to rootnoverify in menu.lst. I'll give that a try.

---

### Post by elpuerco on 2006-09-03
Hi,  I only installed Kubuntu yesterday dualled with XP and everythig was OK.

This morning I started PC and it selected linux by default.  After only a second or two I quickly powered off PC and restarted.

BAD MOVE!  XP partition inaccessible and linux corrupted.  Ahhh lost all my XP stuff?

No, I simply reinstalled Kubuntu from scratch and hey presto instant workin linux and XP all back as normal =D>

---

