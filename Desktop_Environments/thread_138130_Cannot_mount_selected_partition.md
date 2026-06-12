---
title: "Cannot mount selected partition?"
date: 2006-03-01
forum: Desktop Environments
---

### Post by TriggerHappyChewie on 2006-03-01
I recently upgraded to kernel 2.6.12-10-386.  Now when I select that option in grub to boot that Ubuntu kernel, it shows this:

```
 root (hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash

**Error 17: Cannont Mount Selected partition.**
```

I can select the *-9 kernel in grub, and it still gives Error 17.  Is there a way I can roll back to another kernel without having to reinstall?

Another thing, I can view all of my files perfectly in windows using Ext2IFS.

---

### Post by Xian on 2006-03-01
Generally when you upgrade a kernel the previous one is left still installed on your system as a backup. Can you attempt to boot using the older kernel?

---

### Post by TriggerHappyChewie on 2006-03-02
I tried rebooting from the previous kernel, for it is still listed in grub.  However, it is still giving me the same error.

---

### Post by TriggerHappyChewie on 2006-03-05
*Bump*

---

### Post by maka on 2006-06-03
[QUOTE=TriggerHappyChewie]*Bump*[/QUOTE]

i got the same problem...was wondering if you fixed it or if anyone knows how to fix it?

I have dual boot set up with winxp and ubuntu. maybe getting grub to re-detect boot partitions to fix it?  if so, how do i reinstall grub?

---

### Post by sinpalabras on 2007-08-23
i have exactly the same problem, can't boot ubuntu, gparted don't see any partitions, (root ,home swap and xp partitions) but on windows whit ext2ifs i can see them. I dont understand, if i use the live cd i cant mount anything gparted says unaloccated space. please help I can't use ubuntu but if a reinstall i'll loose all off my data (**** dvd burner does not work)

---

### Post by merlinus on 2007-08-23
Try supergrub to boot ubuntu:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

More info on its use:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by sinpalabras on 2007-08-23
Thats were the trouble start.Ii was triing to restore grub after a XP reinstall. I boot from super grub disk and somehow i mess the thing up (fuckit up). I have don it before and it works fine but this time someting went wrong. Maybe is something about EXT2IFS cause i install it before trying to restore grub and maybe it change my partitions name. I think i did somthing wrong at SGD i'll keep on searching.Thank you a lot

---

### Post by merlinus on 2007-08-23
ext2IFS does not mess with your ubuntu partitions.  It allows windows to see them as separate drives (e.g. h:} to be able to write to them.

If supergrub cannot boot ubuntu, perhaps it is best to use a live cd to rescue your data and reinstall.

-merlin

---

