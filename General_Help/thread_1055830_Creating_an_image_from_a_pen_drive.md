---
title: "Creating an image from a pen drive"
date: 2009-01-31
forum: General Help
---

### Post by sameep on 2009-01-31
Hi ,
I would like to create an image of a pen drive the same way we can create an iso image of a cd . I want to use this image to quickly duplicate the same data on a lot of pen drives.

Is that possible ?

Regards,

Sameep

---

### Post by amac777 on 2009-01-31
To make an image of a pendrive, first figure out which drive corresponds to the pen drive by running "mount" from the terminal. On my computer, the pen drive is /dev/sdb1, on your computer this could be different.

Once you know which drive is the pen drive, you can make the image like this: (obviously change the input file parameter to match your pen drive location)

```
dd if=/dev/sdb1 of=diskimage.img
```
The parameter 'if' is input file, and 'of' is the output file. The diskimage.img will be the exact same size as the pendrive.

To write that image to a pendrive, basically reverse the input and output files like this:

```
dd if=diskimage.img of=/dev/sdb1
```

---

### Post by hyper_ch on 2009-01-31
use dd

(1) unmount the pendrive

(2) find out what it's device is (e.g. /dev/sde)

(3) run
```

dd if=/dev/sde of=/home/USER/Desktop/pendrive.iso

```

where USER is your username.

Might be that you need to run this as sudo.

---

### Post by sameep on 2009-01-31
@ amac777 , hyper_ch

Thanks a lot for your reply. Works great .  :D

---

