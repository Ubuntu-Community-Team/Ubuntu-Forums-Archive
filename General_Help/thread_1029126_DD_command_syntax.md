---
title: "DD command syntax"
date: 2009-01-03
forum: General Help
---

### Post by Digitm on 2009-01-03
having some trouble with some path syntax when using the data dump command. Say I have something like this:

$dd if=/dev/hda of=file.iso

but instead i wanted the **output **to be on another partition

of=/dev/sda/file.iso

whats the proper path syntax to make that happen? thanx

---

### Post by jpkotta on 2009-01-03
That has nothing to do with dd.  You have to mount the partition and make sure the output file is somewhere within the newly mounted filesystem.  [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

If you want to copy straight to the partition and completely destroy any data that is there, just give the device node as the output file, e.g.
```
dd if=foo of=/dev/sda1
```

---

### Post by Digitm on 2009-01-03
yes i know you can do a direct transfer from one drive to the next, what i need to know is how to do it with the output still being an iso file.

---

### Post by ByKeLaO on 2009-01-03
Mount the disk you want to save the ISO on by using nautilus (Places->Computer) and then do this:
```
dd if=/dev/hda of=/media/[disk name here]/file.iso
```
Of course, replace [disk name here] with the name of the volume you want to copy it to.

---

### Post by jpkotta on 2009-01-03
I don't think it will be a valid .iso.  As in, if you just copy data straight from a disk, it is not in .iso format.  You need to use something like k3b, nautilus (probably has some kind of "create CD" function), or genisoimage (which probably everything else uses in the end).

---

### Post by Digitm on 2009-01-03
cool, thanks robinjam. "of=/media/[disk name here]/file.iso" was exactly what i was looking for. Havent tried it yet but that looks like it should work.

---

