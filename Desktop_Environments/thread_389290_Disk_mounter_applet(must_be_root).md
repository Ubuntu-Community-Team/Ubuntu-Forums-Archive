---
title: "Disk mounter applet(must be root)"
date: 2007-03-20
forum: Desktop Environments
---

### Post by dixon on 2007-03-20
I've added disk mounter applet to my gnome panel, but when I want unmount(or mount), I get an error : "umount: only root can unmount /dev/hda1 from /media/hda1 "

Also I've got problem with mounting my external HDD(connected through PCMCIA SATA controller) - I can mount it from command line, but it won't show up in "Places" and disk mounter applet, but It's normally mounted in /media/sda1 - I can access the HDD...

My /etc/fstab
```

proc /proc proc defaults 0 0
UUID=2d975ef3-5f6d-4bf7-95cb-a40563931b77 / reiserfs notail 0 1
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
UUID=44432947-84cb-455e-84b9-c0c49cc111b5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by ubix on 2007-03-20
> **dixon said:**
> I've added disk mounter applet to my gnome panel, but when I want unmount(or mount), I get an error : "umount: only root can unmount /dev/hda1 from /media/hda1 "
... o o o ...To the <options> field in  **/etc/fstab**, add the keyword **user** to the filesystem, you wish a regular user to load interactively, just like your **/dev/hdc** has it. Do not miss the comma ie: ```
... **users,**defaults,locale=en_US.UTF-8 ...
```.

---

### Post by dixon on 2007-03-20
THX it's working :)

Still having problem with the 2nd part ...
> Also I've got problem with mounting my external HDD(connected through PCMCIA SATA controller) - I can mount it from command line, but it won't show up in "Places" and disk mounter applet, but It's normally mounted in /media/sda1 - I can access the HDD...

---

