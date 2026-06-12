---
title: "Mounted devices not showing up!"
date: 2005-04-08
forum: Desktop Environments
---

### Post by RastaMahata on 2005-04-08
Just upgraded from warty to hoary. In warty, whenever i went to "computer:///", I could see all my hard drives, even the ones mounted in fstab. Anyhow, since I updated, i haven't been able to see them (although they're still mounted! I can browse the files if I go to /media/blabla).
Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc5       /media/HardDrive    vfat    umask=000       0       0
/dev/hda1       /media/Windows    ntfs    umask=0222      0       0
```

Any ideas?

---

### Post by wfx on 2005-04-08
similary here.
Test in a terminal " sudo /etc/init.d/dbus-1 restart"

---

### Post by telmo on 2005-04-08
No idea whatsoever... my icons keep appearing and disappearing... :S

---

### Post by RastaMahata on 2005-04-08
[QUOTE=wfx]similary here.
Test in a terminal " sudo /etc/init.d/dbus-1 restart"[/QUOTE]
 yep, that seemed to work! but after a reboot (not in X, but computer), I have to do that again to see my mounts.

---

### Post by Cool_dude_Prav on 2005-04-09
Plz tell me on how to automount all my fat32 partitions on Boot..
Also, on how to make it to be shown like a proper drive. I want it to be seen on my desk preferably..

---

### Post by jordanau on 2005-04-09
[QUOTE=Cool_dude_Prav]Plz tell me on how to automount all my fat32 partitions on Boot..
Also, on how to make it to be shown like a proper drive. I want it to be seen on my desk preferably..[/QUOTE]

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by wfx on 2005-04-09
@RastaMahata
I know and i have also post this bug (03.27.2005):
[http://bugzilla.ubuntu.com/show_bug.cgi?id=8269](http://bugzilla.ubuntu.com/show_bug.cgi?id=8269)

Dont know how long it take to fix it?

---

### Post by Cool_dude_Prav on 2005-04-22
[QUOTE=jordanau][http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)[/QUOTE]
 When I try to auto-mount my Extended Fat32 partitions using fstab, it gives me some error...(during boot time) If someone tells me how to see the boot-time errors, I can tell what is wrong for sure...

---

