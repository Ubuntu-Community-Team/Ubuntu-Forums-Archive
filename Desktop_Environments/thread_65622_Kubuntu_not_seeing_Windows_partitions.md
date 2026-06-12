---
title: "Kubuntu not seeing Windows partitions"
date: 2005-09-14
forum: Desktop Environments
---

### Post by Optiker on 2005-09-14
I just installed Kubuntu 5.10 dual booted with Win2000. Everything seemed to go smoothly except there seems to be a sound problem (not going to worry about that now), an error regarding the console font, and the issue I'm writing about, Kubuntu isn't showing my Win2000 partitions.

Whene I installed an earlier version on a different computer with WinXP, it worked fine. I could see all drives in the mnt folder, and by hovering over each, I could get their names. In this case, there is nothing in the mnt folder. Does that mean nothing is mounted, and nothing available to mount?

There are several drive folders in the media folder which I now understand are meant as mounting points, but those are the CDROM drives and floppy - actually there is a floppy and a floppy0, which I don't understand either. I was counting on being able  see the Windows partitions in mnt so I could get their names to edit fstab to have them mounted.

So, how do I go about mounting them? I'd like both C and D-drives mounted. C is NTFS and I don't mind read-only. D is Fat32, so would want read and write.

Thanks in advance for your help.

Optiker

---

### Post by zAo on 2005-09-14
Try
```
sudo fdisk -l
```to discover if your patitions are found.
Try
```
sudo gedit /etc/fstab
``` 
to assign the mount. Dont forget to make the directories and do a 'sudo mount -a'.

---

### Post by Optiker on 2005-09-14
zAo...OK - got it. Seeing both and mounting.

Thanks!
Optiker

---

