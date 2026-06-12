---
title: "EXT3 file system destroyed, ASH: Can't load TTY"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Ranime on 2006-07-16
I used gnomeburner and everything went fine until I tried to close gnomeburner, and got a system hang.

So I resetted the pc and all I got was the ASH-shell and none of my harddrives are mountable.

The exect error I got sounds like this...

```
ASH: Can't load tty, terminating to ash-shell.
Type HELP to view the build-in commands.
#
```

and that's it... Can anyone tell me how I can recovr or restore the filesystem? It's basic EXT3 and i tried all the boot options in the GRUB menu. Is there any way to get X up and running again?

---

### Post by Ranime on 2006-07-17
Well... What can I say... The end of it all is that the superblock of hdb was damaged (I use hda for windows and hdb for ubuntu). End of story. fsck.ext3 was unable to repair the damage. Ended up re-installing the whole. lost 83GB of data ](*,) :cry:

---

### Post by philippe_carlo on 2006-07-17
Wow, any idea what went wrong? Just running a program should not destroy your disk, right? What were you trying to do with gnomeburner?

---

### Post by Ranime on 2006-07-18
I was copying 2 audio cd's. I have only one dvd/cd burner, so it was making immages.

After the last image was finished, I closed gnomeburner and the system freezes. I couldn't even open a terminal (tty1 ~ tty4). I think it was trying to clean up the images, 1.4GB and was writing in the mbr. After I pushed the reset button, the superblock of the drive was scrambled... Game Over :cry:

Physicaly the harddrive is OK, only the data is lost. I re-installed it without any problems. fsck said the drive is ok.

---

