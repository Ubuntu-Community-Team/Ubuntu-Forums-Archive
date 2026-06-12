---
title: "How to add a virtual or emulated Floppy drive in  Ubuntu"
date: 2009-01-10
forum: General Help
---

### Post by praveen.singh18 on 2009-01-10
Hi 

Can any one help me to add a virtual floppy drive? I'm trying to create a custom boot floppy disk to load my custom kernel but my laptop has no floppy drive.

Is there any software I can use or any way ubuntu can emulate a floppy drive?

Thanks

---

### Post by col48 on 2009-04-27
I have a similar question (see the thread I started yesterday about creating a floppy image with no floppy drive).  I have created an image file on a machine with a floppy drive and transferred it to the Ubuntu machine.

I *_think_* all it needs now is to set up /dev/fd0 and point it to my image file instead of where it would point to if it were a physical floppy (/media/floppy or something similar, I guess).  This might make Ubuntu treat the file as if it were a floppy, although the File system inside would not be ext2 (normal Linux) but fat.  Hmmm.

Not really an answer, but it may point the way.  Maybe someone will give an authoritative solution both for you and for me.

---

### Post by col48 on 2009-04-27
Just found this, which may answer it.

[http://ubuntuforums.org/showthread.php?t=570903](http://ubuntuforums.org/showthread.php?t=570903)

---

### Post by TheLions on 2009-04-27
create diskette: (size=bs*count)
```
dd bs=512 count=2880 if=/dev/zero of=imagefile.img
mkfs.msdos imagefile.img
```

and mount it using:
```
sudo mount imagefile.img /media/floppy -o loop
```

---

### Post by col48 on 2009-04-27
Brilliant.

Thanks.

This helps me - I hope praveen singh has not given up on it!

---

