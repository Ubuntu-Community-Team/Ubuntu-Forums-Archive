---
title: "Copying partition from one hd to another"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Fab on 2005-06-13
hi
im not sure if this is the right section, if it is not, some mod please move ;P
anyway, i bought and succesfully mounted into the case a new harddisk, while keeping the old one for windows. the new one is jumped to slave, connected and recognized by bios. i know how to create a new partition, but i wanted to know if there is an easy way to copy the content from the old partition (hda5 in my case) to the new one (hdb1 in my case). i have parted, fdisk and all the standard tools installed.

regards,
Fab

---

### Post by Xian on 2005-06-13
[QUOTE=Fab]i wanted to know if there is an easy way to copy the content from the old partition (hda5 in my case) to the new one (hdb1 in my case). i have parted, fdisk and all the standard tools installed.[/QUOTE]
If you can mount it you can copy it from the command line. Let's say for example that you have mounted those partitions to these paths:

hda5 to  /da5
hdb1 to  /db1

Then it would just be a matter of transferring the data:

```
$ sudo cp -rpfd /da5/* /db1/
```

---

### Post by Fab on 2005-06-13
ty, seems i already found another solution ;)
"dd if=/dev/hda5 of=/dev/hdb1 bs=8k"   seems to work. at least my disk is working for some time now ^_^

---

### Post by jeremy on 2005-06-13
dd takes longer because, if my memory serves me well, it copies the empty space too.

---

### Post by GTvulse on 2005-06-13
[QUOTE=Fab]ty, seems i already found another solution ;)
"dd if=/dev/hda5 of=/dev/hdb1 bs=8k"   seems to work. at least my disk is working for some time now ^_^[/QUOTE]

Yup. That works, but it is like killing a flea with a sledgehammer.

Besides what Jeremy points out, this method works if and only if both hda5 and hdb1 have the same number of blocks allocated, or hdb1 doesn't have an adjacent hdb2 partition sitting there in the disk. Else you are bound to kill some data in the second partition of your disk and, worse, a foobared partition table in the disk superblock....

The *cp(1)* method works, but some versions of *cp(1)* have troble copying sparse files, thus I wouldn't risk it. (**CAVEAT LECTOR**: I have no idea if the cp shipped with hoary has that bug or not). I myself am very partial to *rsync(1)* because it will handle almost anything you throw at it and most importantly, **it copies device and FIFO files cleanly**.

---

