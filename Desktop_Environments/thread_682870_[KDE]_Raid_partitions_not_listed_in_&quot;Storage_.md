---
title: "[KDE] Raid partitions not listed in &quot;Storage Media&quot;"
date: 2008-01-30
forum: Desktop Environments
---

### Post by quilty on 2008-01-30
Hello

I'm running Kubuntu 7.10 and I've set up my software raid successfully. All raid partitions I got are mounted to /media/mdX (1,2,3).
For convenience I would like them to be listed under Storage Media (system:/media/) - any ideas how to get them to show up there?

Thanks,
quilty

---

### Post by jan quark on 2008-01-31
try this

make a new mount point with

```
sudo mkdir /media/mdX (1, 2, 3)
```

and mount your partitions in the new directory

_///// run ```
sudo fdisk -l
``` to get the correct names of the partitions /////_
```

sudo mount /dev/mdX or hda1 ??? /media/mdX (1, 2, 3)
```

---

### Post by quilty on 2008-01-31
Either my English is that bad, that I can't even describe my problem properly or you don't get my point (or both :)).

I have the partitions mounted and running (/dev/md1 -> /media/md1, ...), I even set up a correct fstab to do it for me automatically at startup and everything. They are working perfectly - I'm using them on regular basis.
My problem is that I want those three partitions to show up in the "Storage Media" Part of the KDE bookmarks (Those listed on the left side on a default Dolphin Window). Atm there are only my normal SATA partitions and removable drives listed when in use.

quilty

---

