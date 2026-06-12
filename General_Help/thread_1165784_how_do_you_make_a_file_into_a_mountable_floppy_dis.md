---
title: "how do you make a file into a mountable floppy disk?"
date: 2009-05-21
forum: General Help
---

### Post by spearfish on 2009-05-21
I would like to make a file act like a mountable floppy disk.  Is there any way to do this?

I thought I could just create a file, say, "testfloppy" and then format it, but Linux doesn't seem to have a "format" command.

Then I wanted to run mkfs on the new device, and mount it at /mnt/floppy

The reason is that I'm trying to use this file as a 1.4MB disk image and mount it on a system that doesn't have a real floppy drive.

Thanks!

;)

---

### Post by iissmart on 2009-05-21
Would something like this work?

```
sudo mount -o loop floppy.img /media/floppy/
```

---

### Post by spearfish on 2009-05-21
Hi,

Yeah, the problem I had was with making a .img file.  I found the dd command can do it.  Here's a 1.2MB disk:

dd bs=512 count=2280 if=/dev/zero of=floppy.img
mkfs.msdos floppy.img

That makes the .img file, and then:

sudo mkdir /media/floppy1/
sudo mount -o loop floppy.img /media/floppy1/

That seems to work.  It mounts the file as a floppy disk and you can write files to it.

---

