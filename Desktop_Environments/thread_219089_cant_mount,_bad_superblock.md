---
title: "cant mount, bad superblock?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by siman on 2006-07-19
hello,
i've looked through the forum and found some similar problems, but none with a solution. what happend to me is this:

I dualboot winxp (hda2) and dapper (hdc1). I'm using gag to boot, but everytime I reboot from windows gag is lost and I've to reinstall (via its menu) onto hda. This didnt work today (it complained about hda not being read), but nevertheless I could use the gag from cd and boot into dapper.

While starting dapper it complained about not being able to mount /dev/hda1 and fsck got me the "bad superblock" error message.

this is my fdisk -l output:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       25354   203655973+  83  Linux
/dev/hda2           25355       30400    40531995    7  HPFS/NTFS

```

When i run fsck it says this:

```

simon@silentia:~$ sudo e2fsck /dev/hda
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I've tryed all other backup-superblocks with the -b option, but I get the same error message.

I'v read about win2k messing up ext3, if both are on the same HD and this looks just like it :-((

Is there any chance I can restore the data from hda1?
What about this superblock? Can I just rewrite it to hda1 - like I can do with the MBR?

thanks for any hints...
simon

edit: i tried sudo e2fsck /dev/hda1 (with the 1) aswell.. same error

---

### Post by siman on 2006-07-19
UPDATE: wow... i did a restart and everything is back to normal. THANK YOU UBUNTU. fsck even didnt report any errors. but... very strange behaviour, isnt it? I bet it was windows doing something crazy do the HD. now i'm afraid to start windows :-)


I tried to get more information. cfdisk just says "fatal error accessing drive", but I got this from sfdisk:

```

simon@silentia:~$ sudo sfdisk /dev/hda -l

Disk /dev/hda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  25353   25354- 203655973+  83  Linux
/dev/hda2      25354   30399    5046   40531995    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty


```

Of course there is no hda3,hda4.. I never created those.

Also: I didnt write to ext3 from windows or something stupid. I just use windows for games.

---

