---
title: "tmp folder is tiny"
date: 2009-05-23
forum: General Help
---

### Post by JoelMay on 2009-05-23
I filled up my hard drive completely and some apps were getting errors, I restarted X server not knowing what was going on then it wouldn't let me log in and told me my hard drive was full so I rebooted my computer and I got logged in and deleted some files.  Now my tmp folder says "14.4 KB used" and "984.0 KB free".  I cannot watch YouTube videos or download files with FireFox.  If I can't fix this I might need to reinstall.

Oops, I put this in the wrong header, it should be in Ubuntu.

---

### Post by hansdown on 2009-05-23
Hi JoelMay.

Ummmm, What version of ubuntu are you running?

What are your system specs?

---

### Post by JoelMay on 2009-05-23
I'm running 9.04.  Quad core, 4 GB RAM, about 40 GB HDD partition for Ubuntu, 160 GB HDD.

---

### Post by CatKiller on 2009-05-23
> **JoelMay said:**
> I rebooted my computer and I got logged in and deleted some files. 

Did you delete them, or did you just move them to the Trash?

---

### Post by JoelMay on 2009-05-23
I deleted (shift+delete) them and made sure my trash was empty.

---

### Post by taurus on 2009-05-23
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```

---

### Post by JoelMay on 2009-05-23
I have changed a few things so the output is different today than it was yesterday, not it works, but I'll try to post what I saw yesterday.

Fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f0c3fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41942016    7  HPFS/NTFS
/dev/sda2           10960       14357    27294435    5  Extended
/dev/sda3           14358       19457    40958976    7  HPFS/NTFS
/dev/sda4            5223       10959    46082452+  83  Linux
/dev/sda5           10960       14212    26129691   83  Linux
/dev/sda6           14213       14357     1164681   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Df

```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       44G   33G  9.0G  79% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  348K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  156K  2.0G   1% /dev
tmpfs                 2.0G  292K  2.0G   1% /dev/shm
/dev/sda4              44G   33G  9.0G  79% /media/Ubuntu
overflow                1M    1M   20K  95% /tmp
```

(almost everything on the "/tmp" line is estimated from what I saw yesterday)

---

