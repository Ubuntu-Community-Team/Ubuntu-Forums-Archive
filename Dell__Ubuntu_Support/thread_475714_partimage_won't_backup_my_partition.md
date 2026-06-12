---
title: "partimage won't backup my partition"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by Thorun on 2007-06-16
Hi. 

I have the Dell latitude X1 with Ubuntu Feisty-Fawn installed.
I'm pretty new to the Linux-stuff and i would like to play a lot with different stuff. 
But when something goes wrong it would be nice to have a system-restore-backup i could overwrite my partition (where the os is installed) and start from that point again. 
I have now re-installed Ubuntu 7 times because i messed Emacs up and NTFS-3g support and my fstab-file and some other stuff i just don't know how to repair. 

Therefore i have searched google for some days now (yes - days!) and found several backup-programs. And some friends just told me to do it from the Terminal....

1.
I have now tried to backup from the terminal - with success. But when i restored my backup, i found that it didn't overwrite everything on my partition. E.g. the newest files i had om my computer (and desktop) is called "Y", and the files on my backup file is called "X". I messed up some of the Y-files and wanted to restore my system with everything (including my home-folder) so my computer after the restore only contained "X-files". 
But to my suprise it mixed both the Y- and the X-files - which ended up in a mess!

The goal was to just have X-files and get totally rid of the Y-files.

2. 
I have tried the program called "partimage". Allmost with success. I wrote in the text-menu:
partimage -z0 -f0 save /dev/sda3 /mnt/backup/ubuntu7.04-01

and it started to backup my partition. But from the beginning it told me, that there only was 450MiB free to the image. (i have 5,5GiB free on the partition and i just made a backup of a new ubuntu-install hence ~2GiB). There should be plenty of space to make a backup-file. 

If i could make program backup my sda3 partition to the sda6 partition there wold be 40GiB free space. 
But i can't figure out how to make it backup on another partition?!


Can someone help me with either 1. or 2. ? If both - then i will be wery happy :D

---

### Post by angryfirelord on 2007-06-20
Try looking at this utility instead: [http://www.mondorescue.org/]("http://www.mondorescue.org/")

---

### Post by Nekiruhs on 2007-06-20
My suggestion is [System Rescue CD]("http://www.sysresccd.org/Main_Page"). It has partimage (Which really should be done from a live CD) and many other useful recovery tools (Including X11, so it has a gui). I think why it didn't overwrite all the Y files is because your OS was running, therefore those files were in use. Imagine what would happen if you deleted the kernel while running. To start partimage from the System Rescue CD, just wait till it brings up a root prompt (root@sysreccd:/# or something like that), then type 
```
partimage
```
and do your restore there. If you want a gui, just type 
```
startx
```
You'll get Window Maker ( very very low system reqs), and Firefox 2, Dillo (lightweight webrowser), xterm, gparted, ntfs-3g, and some text editiors. If you want, you can run partimage in xterm, instead of the full screen terminal.

BTW, theres no need to supply those command line arguments. Partimage has a GUI built in, just type partimage by itself.

---

