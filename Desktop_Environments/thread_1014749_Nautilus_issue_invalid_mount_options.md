---
title: "Nautilus issue: invalid mount options"
date: 2008-12-18
forum: Desktop Environments
---

### Post by Shocker on 2008-12-18
Hi Everybody!

Yesterday evening I wanted to set a Ubuntu 8.04.1 to mount a FAT32 partition ("MYPARTITION" ) at each boot time.
With this aim I ended up adding "auto" to the mount options in Nautilus,  right clicking MYPARTITION --> properties from the Places menu. 
Now I receive an error message: invalid mount options trying to mount "MYPARTITION" and I cannot open the properties of MYPARTITION neither.

To fix the problem I tried using gconf-editor but I couldn't find any "MYPARTITION" in the register.

1) How can I restore the default (blank) options?
2) Which is the proper way to mount a partition (FAT32) at each boot time?

P.S.: Does the change affect the fstab file? I couldn't find any backup file (like ~fstab that I supposed to be created in this case) and the file seems to have not been modified lately.

Thanks for any hint!

Shocker

---

### Post by ajgreeny on 2008-12-18
I'm not certain whether things have moved on since this was the instructions given me, but you can automount a fat32 partition at boot by adding this line to your fstab file, appropriately edited (**/dev/hda1** will need changing) to point to the right partition, with the command ```
gksudo gedit /etc/fstab
```

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

I hope this helps, and also that it works without problems.  Gedit should make a backup for you anyway, or do0 that manually first, so you can always restore the old version of fstab if there are any difficulties.

---

### Post by Shocker on 2008-12-18
Thanks ajgreeny for your kind reply.

BTW does anyone lnow any possible solution to fix the Nautilus issue?

I've been searching around the internet with no good results...

---

### Post by ajgreeny on 2008-12-18
No problem.  By the way, did that line in fstab work OK?

The reason I did not give you an answer to your "nautilus issue" is that I can't quite work out what your problem is.  I use a desktop with only one panel, not the gnome default of two, and I add the "Disk mounter" applet to that to mount partitions when I need them, rather than have them mount at boot time.

I realise this is not the way a lot of people use their machines but it suits me, as I seldom need to get into my small windows partition these days, in fact I almost never use it anymore, and I don't want that or an alternative linux distro I have installed (Mint6) mounted when I boot ubuntu.

---

### Post by danielpalos on 2008-12-18
I hope you don't mind my intruding on this conversation, but I would like to ask about what type of applications would need a FATx partition, that could not, alternatively, be run from a windows emulator (e.g. wine)?

---

### Post by Shocker on 2008-12-19
Hi danielpalos,
I just need this FAT 32 Partition in the (unlikely) event of data transfer from Linux to M$... 
Thanks for any additional suggestion

---

