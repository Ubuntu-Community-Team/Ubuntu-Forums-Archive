---
title: "Give all users write privilages to fat32 patition?"
date: 2006-04-08
forum: Desktop Environments
---

### Post by WhiteStool on 2006-04-08
As root, I can write to a fat32 partition, but not with all my other users. All others can only read/execute. How, from root, would I change this so all users have write privilages? The fat32 partition is for a windows dual-boot. I use it just for games, I have only used it once since I installed Ubuntu...

---

### Post by marcos89 on 2006-04-08
i ran  **chmod 7777 -R /media/windows/***

and it worked :-D

---

### Post by christhemonkey on 2006-04-08
You need to edit the line in /etc/fstab so it looks like this
```
sudo gedit /etc/fstab
```
```
/dev/hda?   /media/windows   vfat   user,fmask=0111,dmask=0000   0   0
```
Where hda? is your fat partition.

Now type:
```
sudo mount -a
```

If it gives errors about folder not existing then type:
```
sudo mkdir /media/windows
```

---

### Post by WhiteStool on 2006-04-08
I have it mounted at /windows so how to I find our the hda number?

---

### Post by christhemonkey on 2006-04-08
Run this command: (copy and paste if you like, as it looks kinda scary!)
```
for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done
```
It should give you a list of what hda each partition is and also its format.
So there will be a line saying sometrhing like:
```
/dev/hda1 *         1             638      5124703  b   W95 FAT32
```
And for that example it is hda1 you want.

---

### Post by aysiu on 2006-04-08
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by MarkHn on 2006-04-10
I have a duel boot system WinXP and Ubuntu. I would like to mount a fat32 partition which would give full read and write to all users. Can be used to download files, share files between win XP and Linux, etc.

The line in fstab is:
/dev/hda4 /mnt/hda4 vfat defaults 0 0

This gives root read and write acces, but all other users only have read access.
What should I change to give all users read, write and exexute privilages?

tried 
chmod -R 777 ./hda4
but it didnt work

---

### Post by Ramses de Norre on 2006-04-10
Change ```
/dev/hda4 /mnt/hda4 vfat defaults 0 0
``` to ```
/dev/hda4 /mnt/hda4 vfat defaults,umask=0000 0 0
```

---

