---
title: "Strange HDD problems."
date: 2009-03-17
forum: General Help
---

### Post by Nepharlinack on 2009-03-17
Hello Ubuntu community.

As of last night, I have been unable to access my second hard drive. It started when I was having problems saving to it, so I tried a full reboot. However, on reboot, it took a long time to start up, and after Grub and Ubuntu booted, I got many errors until about 10 minutes later, where I finally got Ubuntu up, however I am unable to access the second drive.

Both GParted and fdisk -l show that the drive is connected and recognized, however GParted shows it as having an unknown file system type whilst fdisk -l gives me an output of

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ea79ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6a31c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux


Unfortunately I will be unable to respond to this thread until later tonight as i'm already quite late for uni, however any help or insight into what is going on is highly appreciated.

Many thanks
Nepharlinack.

---

### Post by taurus on 2009-03-17
Post the outputs of these commands from a terminal.

```
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Nepharlinack on 2009-03-17
> **taurus said:**
> Post the outputs of these commands from a terminal.

```
sudo blkid
cat /etc/fstab
df -h
```

Haha, just thought of blkid before I left, only got my main drive and my sda5. Also got an insane clicking sound until I turned it off. I think i'm gonna write off any chance of reviving that drive.

New question, anyone know of a good file retrieval place in Centeral/Southern Auckland, NZ? :D

---

### Post by jwbrase on 2009-03-17
> **Nepharlinack said:**
>  Also got an insane clicking sound until I turned it off. I think i'm gonna write off any chance of reviving that drive.

Yeah, that definitely sounds like a hard drive crash. It's dead.

---

### Post by Nepharlinack on 2009-03-17
> **jwbrase said:**
> Yeah, that definitely sounds like a hard drive crash. It's dead.

First one ever, still have ones from 10+ years ago that are going strong, only had this one for about 6 months.

What's the likelyhood of getting anything back off it? The vast majority isn't important, but there are a few things that I really wish i'd backed up.

---

### Post by taurus on 2009-03-17
You can try TestDisk to see if you could pull anything off of it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by tgalati4 on 2009-03-17
Look for the paper "200 ways to revive a hard disk"

Some are dubious, others funny.

You only need one method to actually work.

Start with least invasive methods first before fire and ice methods.

There are data recovery websites that have a catalog of sounds.  At least it will point you to the right direction.  Try a google search on your exact model.  Perhaps others have had the same problem.

---

### Post by Nepharlinack on 2009-03-17
Phew, so long as there's a chance, I'd hate to just give up. :D

Many thanks for all the help.

Time to think about backups I suppose, why is it that you only ever think about these things when it's too late? :)

---

