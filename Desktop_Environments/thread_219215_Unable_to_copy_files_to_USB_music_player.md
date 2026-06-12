---
title: "Unable to copy files to USB music player"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Mr. Sinister on 2006-07-19
I have a 1GB samsung USB music player. Here's the fdisk output for it:
```
Disk /dev/sde: 1041 MB, 1041367040 bytes
227 heads, 56 sectors/track, 160 cylinders
Units = cylinders of 12712 * 512 = 6508544 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         160     1016932    b  W95 FAT32
```

When I try to copy files to it, it stops less than halfway through and says the disk is full. But according to df it isn't.

```
$ df /media/sde1/
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sde1              1016656    440496    576160  44% /media/sde1/
$ cp .bash_history /media/sde1/
cp: cannot create regular file `/media/sde1/.bash_history': No space left on device
```

I just got the player a couple weeks ago, and I've never been able to copy a full gigabyte to it.
Has anybody here run into a similar problem, or know a way to fix it?
Thanks.

---

### Post by briguy on 2006-07-19
Do a ls -a and check to see if there is a .Trash1000 directory or something like it.  There may be files in your trash folder!  This happens to me all the time...:rolleyes:

---

### Post by Mr. Sinister on 2006-07-19
No, there are no hidden directories.
If hidden directories (or any other type of file) were taking up space, they'd affect the output of df.

---

