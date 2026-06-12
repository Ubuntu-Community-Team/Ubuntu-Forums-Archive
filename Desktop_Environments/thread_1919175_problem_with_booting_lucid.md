---
title: "problem with booting lucid"
date: 2012-02-02
forum: Desktop Environments
---

### Post by cy3a on 2012-02-02
i have lucid on my computer almost 2 years, and it worked just fine until few days ago. suddenly it can't boot, after grub it stops and put the message:
```
gave up waiting for root device. common problems:
 - boot args(cat /proc/cmdline)
 - check rootdelay= (did the sysstem wait long enough?)
 - check root= (did the system wait for the right device?)
 - missing modules(cat /proc/modules; ls /dev)
 ALERT! /dev/disk/by-uuid/b2ecd283-5fb4-4597-ade5-c9c8cb81bda1 does not exist. dropping to shell!
 busybox v1.13.3(ubuntu 1:1.13.3-1ubuntu11) build-in shell (ash)
 enter 'help' for a list of build-in commands.
 (initramfs)
```
i already asked in serbian forum, and with their help i checked root=, rootdelay= and ls/dev/disk/by-uuid. in all of these cases root exists and its uuid is the one that is written in the message above.
can anyone tell me what should i do next?
thanx!

---

### Post by sudodus on 2012-02-02
Hi

Do you have an Ubuntu install CD or USB drive? In that case, boot a live session from it and see if you can mount the partition with that UUID. Then you can unmount it and run e2fsck to look for and if possible repair errors. Read ```
man e2fsck
```

If you have no such CD or USB drive, try to get one (make it yourself with another computer or ask some friend to download an iso file and make a boot CD or USB from it)!

Good luck :-)

---

### Post by cy3a on 2012-02-02
do i run e2fsck from live session, after unmount root partiton?

---

### Post by sudodus on 2012-02-02
> **cy3a said:**
> do i run e2fsck from live session, after unmount root partiton?
Yes, e2fsck should never work on a mounted partition, because a write operation from another program would make it corrupt.

---

### Post by cy3a on 2012-02-02
result is:
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 615258/6537216 files, 23989709/26123535 blocks
```
it seems that filesystem is ok, what should i do next?

---

### Post by sudodus on 2012-02-02
> **cy3a said:**
> result is:
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 615258/6537216 files, 23989709/26123535 blocks
```
it seems that filesystem is ok, what should i do next?
Sometimes you need to force it to check thoroughly
```
sudo e2fsck [COLOR="Red"]**-f**[/COLOR] /dev/sda5

``` and if OK, you can be assured that the file system is OK. So we must look for the problem somewhere else ...

---

### Post by cy3a on 2012-02-02
i can't understand this report:
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  615258 inodes used (9.41%)
   20900 non-contiguous files (3.4%)
     606 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 44631/1429/1
23989709 blocks used (91.83%)
       0 bad blocks
       2 large files

  497871 regular files
   81552 directories
      58 character device files
      26 block device files
       0 fifos
     671 links
   35740 symbolic links (30955 fast symbolic links)
       2 sockets
--------
  615920 files

```
is this mean that root partition is ok?

---

### Post by sudodus on 2012-02-02
Yes, I think it is OK :-)

Next you can check with ```
sudo blkid
``` that the partition really has the same number as what is not found by grub. If it is the same, and still not found, maybe you should try to reinstall grub.

Look for 'Reinstalling GRUB 2 from LiveCD' in the following link
[_[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1195275[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1195275")

---

