---
title: "Fstab question + CDROM automounting."
date: 2005-07-23
forum: Desktop Environments
---

### Post by bravo_elf on 2005-07-23
1)  I've mounted my NTFS dive in Kubuntu, like it was expained in "Starter Guide" but sometimes when I restarting my laptop I see this message :
[color=green]"[mntent]: warning: no final newline at the end of /etc/fstab"[/color]

Does it sufficient one or I just dont need to pay attention?

2) I read the Starter Guide about how to manually mount CDROM, next time I've booted my computer it was unmounted again so how do I can to automate this procces? what do I need write in fstab? (my CDROM is placed on /media/cdrom0)

Tnx for the help

---

### Post by adwait on 2005-07-23
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

This is a line in my fstab to mount the cd rom.

For your first question, it is necessary that there be a blank line at the end of /etc/fstab. If you want that error to go away, just open it up with
sudo gedit /etc/fstab

and add a blank line at the end.

---

