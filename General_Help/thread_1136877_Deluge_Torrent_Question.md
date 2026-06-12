---
title: "Deluge Torrent Question"
date: 2009-04-25
forum: General Help
---

### Post by qjmoss on 2009-04-25
I'm currently running the Deluge torrent client, I've been having some errors recently.

Here's the two errors that I see come up with most of my torrents.


Permission denied

No such file or directory


Is there a simple fix to this, or did I mess something up big time =/

Also, a little more information.


I'm saving all my data to my external hard drive.

My friend said that if it is formatted in FAT32, that you can't save files bigger than a certain size.

Is this my problem?


any information with help.

Thank you for your time

---

### Post by mikewhatever on 2009-04-25
I've experienced the fat32 limitation problem once or twice. When Deluge tries to allocate more then 4GB for a file, an error comes up that there is no space. It seems to be different in your case. When exactly do you see the errors? Can you post the output of **sudo fdisk -l** to verify the file system.

---

### Post by qjmoss on 2009-04-25
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab00e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux
/dev/sda2           19085       19457     2996122+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)

```

---

### Post by qjmoss on 2009-04-25
l

---

### Post by mb_webguy on 2009-04-25
Please wait 12-24 hours before bumping a post.

What permissions are you using to mount the FAT32 partition?

---

### Post by mikewhatever on 2009-04-25
Well, sdb1 is fat32 indeed. Can you now tell us when you see the errors.

---

