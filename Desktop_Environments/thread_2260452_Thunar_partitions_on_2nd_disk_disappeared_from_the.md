---
title: "Thunar: partitions on 2nd disk disappeared from the left pane"
date: 2015-01-12
forum: Desktop Environments
---

### Post by Kirkx on 2015-01-12
The partitions on the second disk would always appear in Thunar in the left pane under Devices. I have just noticed that it's no longer the case, only partitions from the first disk are shown by default. Was this change part of some latest updates or is something broken in my settings, and how to get those partitions from /dev/sdb showing again?

[http://i.imgur.com/CsRMMhc.png](http://i.imgur.com/CsRMMhc.png)

---

### Post by kerry_s on 2015-01-12
you probably just unmounted it by accident, you can remount it from terminal or just restart your pc.

---

### Post by Kirkx on 2015-01-12
No, no accident. I have noticed this just after cold PC start and booting to Xubuntu. I have four partitions on Disk-2 and use them for routine maintenance (backups, etc.) so I'm used to looking at them from time to time. If no one else has experienced this problem then I will later look at my bootloader files, maybe I've messed up something there.

---

### Post by Kirkx on 2015-01-12
It looks like some kind of bios or hardware driver problem, probably related to my latest Grub4Dos bootlader tests that involved mapping disk-2 to disk-1, etc. Any partition from disk-2 can be easily mounted from terminal but in Thunar it shows as external drive that can only be disconnected by administrator:

[http://i.imgur.com/RUBdiUd.png](http://i.imgur.com/RUBdiUd.png)

Maybe this will clear up on its own after a few days and several cold starts.

---

### Post by ajgreeny on 2015-01-12
Just out of interest, why are you using Grub4Dos instead of the default grub2?

I admit I don't know much about Grub4Dos other than the fact that it makes life a bit more difficult for some users, and the support you will get from the forum is likely to be fairly limited.

---

### Post by kerry_s on 2015-01-12
> **Kirkx said:**
> It looks like some kind of bios or hardware driver problem, probably related to my latest Grub4Dos bootlader tests that involved mapping disk-2 to disk-1, etc. Any partition from disk-2 can be easily mounted from terminal but in Thunar it shows as external drive that can only be disconnected by administrator:

[http://i.imgur.com/RUBdiUd.png](http://i.imgur.com/RUBdiUd.png)

Maybe this will clear up on its own after a few days and several cold starts.


funny, mine works the opposite way. i have to punch in my password to mount my second drive, but no password is required to unmount it. 
my second drive only has a swap partition & the rest is ext4 for storage of things i want to save. i don't add it to fstab or nothing, it's just always there after install. i been distro hopping all week.

---

### Post by Kirkx on 2015-01-12
If the problem doesn't get fixed on its own after a few cold restarts then I will have to add those partitions to /etc/fstab.

> ajgreeny: Just out of interest, why are you
using Grub4Dos instead of the
default Grub2?

Please refer to the last paragraph (3) in the last post here:

[http://ubuntuforums.org/showthread.php?t=2248645#10](http://ubuntuforums.org/showthread.php?t=2248645#10)

Grub4Dos has its own forums:
[http://www.reboot.pro/forum/66-grub4dos/](http://www.reboot.pro/forum/66-grub4dos/)

---

### Post by Kirkx on 2015-01-23
The problem somehow got fixed on its own. All unhidden partitions on the second disk are back, shown in Thunar in the left pane under Devices. My theory is that they have reappeared after the unallocated space in Disk-2 was moved from the primary partition area to inside the extended partition. I have also done several cold restarts and forced power offs, but that alone didn't do the trick in the past.

[http://i.imgur.com/c447jm2.png](http://i.imgur.com/c447jm2.png)

---

