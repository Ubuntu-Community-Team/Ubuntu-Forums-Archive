---
title: "Target Filesystem Doesn't Have /sbin/init"
date: 2009-05-30
forum: General Help
---

### Post by CaptainEvilStomper on 2009-05-30
First I think I should explain exactly what happened. I've been trying to get dual-booting working with Ubuntu and Windows XP, and I finally figured out that the reason I couldn't get Windows to boot using Grub was that Grub was on a different hard drive. That being the case, I figured I'd just copy Grub over to the Windows hard drive, so I made a new ext3 partition, copied the contents of my /boot partition over to it, and updated my fstab and Grub menu file. I tried booting to Ubuntu first to make sure I didn't break anything, and everything worked. After that I tried Windows, which also worked.

Here's where it gets confusing. After the initial test boot into Windows, I tried booting back to Ubuntu, and it suddenly stopped working. I tried recovery mode and using an earlier kernel and I'm still getting the same error. Here's what it's giving me:

```
kinit:name_to_dev_t(/dev/disk/by-uuid/######...)
kinit: trying to resume from /dev/disk/by-uuid/#####...
kinit: No resume image, doing normal boot
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg
```

...at which point the BusyBox shell comes up. Can anyone help me out here? I'm completely lost on this one and so far Google has been no help.

---

