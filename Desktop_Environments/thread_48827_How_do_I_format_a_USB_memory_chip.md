---
title: "How do I format a USB memory chip"
date: 2005-07-14
forum: Desktop Environments
---

### Post by tux-curious on 2005-07-14
I've been looking at commands and I just want to double check something.

I want to format my 256mb memory chip card thingy (SanDisk Cruzer Mini).

Is fdformat the best command to use or is there something better?

Thx,

Steven  ](*,)

---

### Post by varunus on 2005-07-14
Why do you want to format it?  Can't you just open a terminal, cd to the directory, and type "rm -rf *" to erase the contents?  (Be VERY CAREFUL with that command; make sure you're in the right folder, or it will delete EVERYTHING.)

I suppose you could use mkfs.vfat if you wanted to format.  To use it, type:

```
sudo mkfs.vfat /dev/thenameofyourusbstick
``` 

To get the name of your USB stick, type "mount" in a terminal, and it should be something like /dev/sda1 or /dev/sda...

Be very careful with both of these commands, as if you make a typo, you can screw up your entire system by deleting the wrong area.

---

### Post by dataw0lf on 2005-07-14
Or, if it's going to be exclusively used on a Linux system:

mke2fs -j /dev/<whatever, probably sda or something similar>

for an ext3 filesystem.

---

