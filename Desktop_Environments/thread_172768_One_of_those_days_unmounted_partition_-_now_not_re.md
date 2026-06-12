---
title: "One of those days: unmounted partition - now not recognised..."
date: 2006-05-09
forum: Desktop Environments
---

### Post by J77 on 2006-05-09
I'm having a bad day :( 

'Accidently' I have unmounted an empty partition called /home2

I can't seem to get it back...

There were some warnings when I rebooted and I can't mount it (and therefore access it) anymore.

Can anyone tell me how to solve this...

It still is shown in fstab.

edit: in dmesg it says: Can't find ext3 filesystem on sdb5 (where home2 was mounted before)

---

### Post by cgjones on 2006-05-09
What exactly have you tried? And what where the error messages? Also, if you could post the contents of fstab, it might help.

---

### Post by J77 on 2006-05-09
**fstab**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda7       /data           ext3    defaults        0       2
/dev/sdb6       /home           ext3    defaults        0       2
/dev/sdb5       /home2          ext3    defaults        0       2
/dev/sda6       /tmp            ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

**dmesg**

```
VFS: Can't find ext3 filesystem on dev sdb5.
```

**df**

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             14421376   2580340  11108472  19% /
tmpfs                  1619580         0   1619580   0% /dev/shm
/dev/sda1                90297     20024     65456  24% /boot
/dev/sda7             28834684    131260  27238704   1% /data
/dev/sdb6             41714332  10737536  28857828  28% /home
/dev/sda6             14421344    131304  13557480   1% /tmp

```

---

### Post by cgjones on 2006-05-09
Which partition was / on before?

---

### Post by J77 on 2006-05-11
/ is working fine, it's on /dev/sda5

It's /home2 that I lost. This was on the second disk at /dev/sdb5

It still shows up in fstab but I can't mount it.

---

### Post by J77 on 2006-05-11
bit more...

On start up I get the following error:

**fsck failed. Please repair manually.**

However, I've been skipping this by using Ctrl-D.

---

### Post by syg00 on 2006-05-11
If it was empty, why don't you just rebuild the file system and remount it ???.

Sounds like you have nothing to lose.

---

### Post by J77 on 2006-05-11
[QUOTE=syg00]If it was empty, why don't you just rebuild the file system and remount it ???.

Sounds like you have nothing to lose.[/QUOTE]Can you do that for indivdual disks?

I have lots of important work on the first disk.

---

### Post by cgjones on 2006-05-11
If there is nothing important on /dev/sdb5, you should be able to reformat it. From what you've told us, it certainly sounds like the filesystem on /dev/sdb5 is messed up. I would try either fsck or just reformat it with whatever filesystem you want on there.

---

### Post by J77 on 2006-05-17
Fixed it by running **fsck -y /dev/sdb5** when prompted the above :)

---

