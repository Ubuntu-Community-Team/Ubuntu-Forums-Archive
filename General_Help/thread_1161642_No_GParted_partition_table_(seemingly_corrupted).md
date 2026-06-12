---
title: "No GParted partition table (seemingly corrupted)"
date: 2009-05-16
forum: General Help
---

### Post by eternicode on 2009-05-16
Earlier today I reinstalled WinXP into an existing partition on my 60GB drive.  After getting it all set up, I reinstalled GRUB.  Then I went to gparted to change some partition sizes, and it showed the entire disk as unallocated.  I can boot exactly like I've always been able to, but gparted can't see the partitions.

There was one point during all the Windows Updates that I got an "error loading os" message, and had to boot the windows CD and run "fixboot" before Win would boot again.  So that may have something to do with the table loss.

fdisk:
```
andrew@Ximplix:~$ sudo fdisk -lu /dev/sda
omitting empty partition (5)

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders, total 114270345 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    25286309    12602992+   7  HPFS/NTFS
/dev/sda3        25286310   107330264    41021977+   5  Extended
/dev/sda4        25334505    29527469     2096482+   b  W95 FAT32
/dev/sda5        25286436    25334504       24034+  83  Linux
/dev/sda6        29527533    40017914     5245191    b  W95 FAT32
/dev/sda7        40017978    90028259    25005141   83  Linux
/dev/sda8        90028323   106800119     8385898+  83  Linux
/dev/sda9       106800183   107330264      265041   82  Linux swap / Solaris
```

sfdisk:
```
andrew@Ximplix:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id=de
/dev/sda2 : start=    80325, size= 25205985, Id= 7, bootable
/dev/sda3 : start= 25286310, size= 82043955, Id= 5
/dev/sda4 : start= 25334505, size=  4192965, Id= b
/dev/sda5 : start= 25286436, size=    48069, Id=83
/dev/sda6 : start= 29527533, size= 10490382, Id= b
/dev/sda7 : start= 40017978, size= 50010282, Id=83
/dev/sda8 : start= 90028323, size= 16771797, Id=83
/dev/sda9 : start=106800183, size=   530082, Id=82
```

According to everything I've found on these forums, I have a corrupted partition table.  And, apparently, the only way to fix it is to have some sfdisk guru fix me up with a partition-description file to pass into sfdisk.

What I'm hoping for here is two things: 1) a file to pass to sfdisk to fix my partition table, and 2) an explanation of how exactly you came up with that file (preferably explained in a way that I can duplicate the effects myself, with a different drive, should I ever need to :D ).  I've tried comparing others' sfdisk output with the files they were given, but I'm having trouble making sense of them.

Thanks!

---

### Post by quixote on 2009-05-16
Scary stuff.  Installing Windows second often leads to it stepping all over your hard drive.  I don't know how to solve your problem, but when I had a similar one, I found testdisk.  It rebuilt a partition table on an SDcard, and all I had to do was answer "yes" a few times. :-D

Testdisk is in synaptic, but if I were you I 'd probably try not to use that drive much until the partition table was healthy again.  Maybe boot off a USB or liveCD that has testdisk on it.

---

### Post by eternicode on 2009-05-17
quixote, the thing is, I seem to recall reinstalling WinXP before, on the same machine, and it worked fine.  And I know for a fact that I installed the Win7 7000 beta on this same partition, and it worked perfectly (after restoring grub, of course), but that may just be because it's a newer OS.  First time this has ever happened.

I'll check out this testdisk you mentioned, thanks.

---

### Post by quixote on 2009-05-17
I think it's pretty random whether the older Windows step on other installs or not.  I gather they just ignore everything else.  Don't know about Win7.  Be good if M$ decided to be a bit more respectful of people's setup!

---

### Post by eternicode on 2009-05-19
Well, I tried the testdisk solution.  It was able to recover all but my shared FAT32 partition, which was fairly easy to backup and restore once I reformatted it with gparted.

After the recover, I found out that my entire root partition was whacked; ran fsck on it, and it nearly wiped it clean clearing bad inodes (ended up wiping almost 4GB of data), so needless to say I took the opportunity to upgrade to Jaunty.  Fortunately, I've spent the past few days backing up my system mods so that I could upgrade, so I had all the stuff I needed (like smb.conf, fstab, etc) to get back up again.

I also decided to start with a fresh home directory (after using this same home directory since the time I started Feisty!), so the next major task is getting my DE back to the way I like it.

The worst part was reinstalling grub... I have a separate grub partition set up to boot to either linux (via configfile directive) or windows (via chainloader), but for some reason the configfile path would always lead to "file not found".  Setting my Kubuntu root as the grub root works -- not the way I like it, but it works.

Not the best results I could've hoped for, but certainly better than the alternative.  Thanks.

I still haven't seen what it's done to my win partition... I'm almost scared to look!

---

### Post by quixote on 2009-05-19
Glad it sort-of worked :-)

Just a note re Jaunty: 

There seems to be a pretty serious issue for some of us 64-bit users (all gnome, I think.  Not sure. Also not sure whether it's been reported by any 32-bit users.  Another also: I have jaunty running on a Dell, and have no issues on that machine.)  

Random filesystem corruption happens that requires a reboot from LiveCD and running fsck on the affected partition.  It's a pain, and when it crashes, you lose what you're working on.  So far, none of us have lost data, though.  Recovery with fsck is successful. There's a thread about it here: [http://ubuntuforums.org/showthread.php?t=1149563&highlight=filesystem+corruption](http://ubuntuforums.org/showthread.php?t=1149563&highlight=filesystem+corruption)  No solutions, though.

Good luck on the windows partition!  (The "fixmbr" command from recovery console can be a useful one, if the mbr is the problem.)

---

### Post by eternicode on 2009-05-19
Thanks for the heads-up.  I'm using 32bit, so I'll keep an eye out for it.  All the more reason to get my bootable flash drive back up and working.  As for the win partition, I was using qemu from the livecd during my grub wars, and afaict windows was booting fine there.  Not a big deal if it doesn't, though, I'll just reinstall it again :D

---

