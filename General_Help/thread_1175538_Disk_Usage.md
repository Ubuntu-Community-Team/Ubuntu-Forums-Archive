---
title: "Disk Usage"
date: 2009-06-01
forum: General Help
---

### Post by MichaelSammels on 2009-06-01
Hmm, I wouldn't say this is a bug, but it's rather annoying.

The folder /media contains all my drives. Obviously the drives sda1, sda2 and sda5 my Linux Partitions and Swap.

```
michael@ubuntu-linux:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e236c5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      181101  1454693751   83  Linux
/dev/sda2          181102      182401    10442250    5  Extended
/dev/sda5          181102      182401    10442218+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x666e6b55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6dd15b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS
michael@ubuntu-linux:~$ 

```

[Screenshot 6]("http://www.mikewonder.net/images/Screenshot-6.png")

---

### Post by munky99999 on 2009-06-01
That's very unusual. The thing is... I'm having the exact opposite problem atm; and only discovered it because of this thread. Except the disk usage analyser is saying the drive is larger as opposed to smaller.

Ofnote this is entirely off a live session.

---

### Post by drs305 on 2009-06-01
Remvoable drives are by default mounted in /media. Disk Usage Analyzer (DUA) will always show the /media folder, and since these externals or other partitions are mounted in /media they are reflected there. It would appear that your system partition contains very little compared to the other drives you have mounted. Notice /home looks empty but it does contain .7% of your space - it's just too small to register graphically.

The top entry of DUA will always show full, by the way. If you don't want to see the partitions mounted in /media, you can do a few things. I don't see DUA listing your sda drive as part of media however.

You can change what DUA displays is to go to DUA's menu, Edit, Preferences and untick the /media folders of the partitions you don't want information on.

Another way is to close out all your apps and then run "sudo umount -a" which will attempt to unmount *all* the partitions. You will get busy messages as it fails to unmount system partitions. When it is finished, you should be left with only system partitions mounted and /media will be empty.

---

### Post by MichaelSammels on 2009-06-01
So is this a problem? I get two readings from different places. If you go to Places -> Computer, right click Filesystem, you *may* get a different result. See the attached image for my result.

[Screenshot 7]("http://www.mikewonder.net/images/Screenshot-7.png")

---

### Post by MichaelSammels on 2009-06-01
@drs305: that worked :)

---

