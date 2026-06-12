---
title: "ubuntu not reading other partitions"
date: 2006-02-25
forum: Desktop Environments
---

### Post by sdb on 2006-02-25
I have my music on a fat 32 partition, and unless I mount it each time I want to use it ubuntu doesn't see it. 
please help me solve this challenge.

thank you

---

### Post by Irony on 2006-02-25
From [http://ubuntuguide.org/#automountfat;](http://ubuntuguide.org/#automountfat;)

[PHP]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/PHP]

This makes a directory in your media file called windows. You then back up your fstab file. You then edit your fstab file adding;

[PHP]/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0[/PHP]

This assumes hda1 is where your fat32 is - to locate your fat32 do;
[PHP]
sudo fdisk -l
[/PHP]

Once you're done save the fstab file and close it. Remount it by doing;

[PHP]sudo mount -a[/PHP]

---

### Post by aysiu on 2006-02-25
[QUOTE=Irony]You then edit your fstab file adding;

```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```[/QUOTE] The only thing I would caution: Breezy seems to default to adding all partitions to /etc/fstab but with defaults. For example, your /etc/fstab file may already have this entry: ```
/dev/hda1 /media/hda1 vfat defaults
``` If that's the case, don't *add* a new line--simply replace your old line with the line Irony gave.

---

### Post by Irony on 2006-02-25
Actually I changed my fat32 to;

[PHP]/dev/hda1       /media/windows  vfat    defaults,umask=000  0       0[/PHP]

Because during boot-up it would complain about utf8 - it would still boot-up fine though.

As aysiu says replace your line (rather than add to it) if you already have one.

---

### Post by aysiu on 2006-02-25
[QUOTE=Irony]Actually I changed my fat32 to;

```
/dev/hda1       /media/windows  vfat    defaults,umask=000  0       0
```

Because during boot-up it would complain about utf8 - it would still boot-up fine though.[/quote] Doesn't *defaults* mean it won't be able to be read by regular users, only root? By the way, the complaining about utf8 you can ignore.

---

